<template>
  <v-row>
    <!-- Panel de filtros -->
    <v-col
      cols="12"
      md="4"
    >
      <v-card
        class="pa-4"
        elevation="2"
      >
        <v-card-text class="text-h6">
          Filtro de Producto
        </v-card-text>

        <v-select
          v-model="categoria"
          label="Categoría"
          :items="categorias"
          clearable
        />

        <v-btn
          color="red"
          block
          class="mt-4"
          @click="resetFiltros"
        >
          Reiniciar Filtros
        </v-btn>
      </v-card>
    </v-col>
    <v-col
      cols="12"
      md="8"
    >
      <v-card
        class="pa-4"
        elevation="2"
      >
        <v-text-field
          v-model="search"
          label="Buscar producto"
          prepend-inner-icon="mdi-magnify"
          variant="outlined"
          hide-details
          single-line
          clearable
          class="mb-4"
        />

        <v-data-table
          :headers="headers"
          :items="filteredItems"
          :search="search"
        >
          <template #item.imagen="{ item }">
            <img
              :src="getImageUrl(item.imagen)"
              :alt="`Imagen de ${item.nombre}`"
              height="64"
              width="64"
              cover
              class="my-2 rounded elevation-2"
            >
          </template>
          <template #item.actions="{ item }">
            <EditInventario :item="item" />
          </template>
        </v-data-table>
      </v-card>
    </v-col>
    <!-- Componente modal-->
    <AddInventario />
  </v-row>
</template>

<script setup>
import { ref, computed } from 'vue'
import AddInventario from '@/components/Inventario/AddInventario.vue'
import EditInventario from '@/components/Inventario/EditInventario.vue'
const search = ref('')
const categorias = ['Todos', 'mecanica', 'electronica', 'papeleria']
const categoria = ref(null)
const headers = [
  {
    title: 'Presentación',
    key: 'imagen'
  },
  {
    title: 'Nombre',
    key: 'nombre' },
  {
    title: 'Descripción',
    key: 'descripcion'
  },
  {
    title: 'Categoría',
    key: 'categoria',
    align: 'end'
  },
  {
    title: 'Marca',
    key: 'marca',
    align: 'end'
  },
  {
    title: 'Unidad de medida',
    key: 'unidadmedida',
    align: 'end'
  },
  {
    title: 'Acciones', 
    key: 'actions',
    align: 'end'
  }
]

const items = ref([
  {
    id: 1,
    nombre: 'Chupones de grasa',
    descripcion: 'Información breve para alburear a alguien',
    categoria: 'mecanica',
    marca: 'doña chonita',
    unidadmedida: '1pz',
    imagen: 'logo.png'
  },
  {
    id: 2,
    nombre: 'Multímetro digital',
    descripcion: 'Herramienta para medir voltaje y corriente',
    categoria: 'electronica',
    marca: 'Fluke',
    unidadmedida: '1pz',
    imagen: '1.jpg'
  },
  {
    id: 3,
    nombre: 'Resma de hojas',
    descripcion: '500 hojas tamaño carta',
    categoria: 'papeleria',
    marca: 'Chamex',
    unidadmedida: '1resma',
    imagen: '1.jpg'
  }
])

const getImageUrl = (img) => {
   
  return new URL(`../assets/${img}`, import.meta.url).href
}

const filteredItems = computed(() => {
  if (!categoria.value || categoria.value === 'Todos') return items.value
  return items.value.filter(item => item.categoria === categoria.value)
})

const resetFiltros = () => {
  categoria.value = null
  search.value = ''
}
</script>
