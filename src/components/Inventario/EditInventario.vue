<template>
  <v-dialog
    v-model="dialog"
    max-width="500"
  >
    <template #activator="{ props }">
      <v-btn
        v-bind="props"
        color="medium-emphasis"
        icon="mdi-pencil"
        size="medium"
      />
    </template>
  
    <v-card title="Editar producto">
      <template #text>
        <v-row class="pa-4">
          <v-col cols="12">
            <div
              class="image-preview d-flex align-center justify-center"
              style="border: 2px dashed #ccc; height: 200px; background-color: #f9f9f9;"
            >
              <v-img
                v-if="imagePreview"
                :src="imagePreview"
                height="100%"
                width="100%"
                cover
              />
              <span
                v-else
                class="text-grey"
              >Vista previa de la imagen</span>
            </div>
  
            <v-file-input
              v-model="editedProduct.imagen"
              accept="image/*"
              label="Seleccionar imagen"
              prepend-icon="mdi-camera"
              variant="outlined"
              class="mt-4"
              :show-size="false"
              :multiple="false"
              hide-details
            />
          </v-col>
        </v-row>
  
        <v-row>
          <v-col cols="12">
            <v-text-field
              v-model="editedProduct.name"
              label="Nombre"
            />
          </v-col>
          <v-col cols="12">
            <v-textarea
              v-model="editedProduct.descripcion"
              label="Descripción"
            />
          </v-col>
          <v-col
            cols="12"
            md="6"
          >
            <v-select
              v-model="editedProduct.categoria"
              :items="['mecanica', 'electronica', 'papeleria']"
              label="Categoría"
            />
          </v-col>
          <v-col
            cols="12"
            md="6"
          >
            <v-text-field
              v-model="editedProduct.marca"
              label="Marca"
            />
          </v-col>
          <v-col
            cols="12"
            md="6"
          >
            <v-text-field
              v-model="editedProduct.unidadmedida"
              label="Unidad de medida"
            />
          </v-col>
        </v-row>
      </template>
  
      <v-divider />
  
      <v-card-actions>
        <v-spacer />
        <v-btn
          text="Cerrar"
          @click="closeDialog"
        />
        <v-btn
          color="primary"
          text="Guardar"
          @click="emitChanges"
        />
      </v-card-actions>
    </v-card>
  </v-dialog>
</template>
  
  <script setup>
  import { ref, watch } from 'vue'
  
  const props = defineProps({
    // eslint-disable-next-line
    item: Object
  })
  const emit = defineEmits(['update'])
  
  const dialog = ref(false)
  
  const editedProduct = ref({
    id: null,
    name: '',
    descripcion: '',
    categoria: '',
    marca: '',
    unidadmedida: '',
    imagen: null
  })
  
  const imagePreview = ref(null)
  
  // Cargar datos al abrir el modal
  watch(dialog, (val) => {
    if (val && props.item) {
      editedProduct.value = {
        id: props.item.id,
        name: props.item.nombre,
        descripcion: props.item.descripcion,
        categoria: props.item.categoria,
        marca: props.item.marca,
        unidadmedida: props.item.unidadmedida,
        imagen: null
      }
    if (props.item.imagen) {
      imagePreview.value = new URL(`../../assets/${props.item.imagen}`, import.meta.url).href
    }
    } 
  })
  
  watch(() => editedProduct.value.imagen, (newImage) => {
    if (newImage && newImage instanceof File) {
      imagePreview.value = URL.createObjectURL(newImage)
    }
  })
  
  function closeDialog() {
    dialog.value = false
  }
  
  function emitChanges() {
    emit('update', { ...editedProduct.value })
    dialog.value = false
  }
  </script>
  