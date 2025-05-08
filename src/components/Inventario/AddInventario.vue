  <template>
    <v-dialog
      v-model="dialog"
      max-width="500"
    >
      <template #activator="{ props }">
        <v-btn
          v-bind="props"
          color="medium-emphasis"
          text="Añadir Inventario"
        />
      </template>

      <v-card title="Añanir Producto">
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
            @click="dialog = false"
          />
        </v-card-actions>
      </v-card>
    </v-dialog>
  </template>

  <script setup>
  import { ref, watch } from 'vue'

  const dialog = ref(false)

  const editedProduct = ref({
    name: null,
    descripcion: null,
    categoria: null,
    marca: null,
    unidadmedida: null,
    imagen: null,
  })

  const imagePreview = ref(null)

  watch(() => editedProduct.value.imagen, (newImage) => {
    if (newImage && newImage instanceof File) {
      imagePreview.value = URL.createObjectURL(newImage)
    } else {
      imagePreview.value = null
    }
  })
  </script>
