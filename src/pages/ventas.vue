<template>
  <v-container>
    <v-row>
      <v-col
        cols="12"
      >
        <v-card>
          <v-card-title>Ventas</v-card-title>
          <v-card-text>
            Aquí puedes gestionar las ventas de tu negocio.
          </v-card-text>
        </v-card>
      </v-col>

      <v-row class="mb-2">
        <v-col cols="12">
          <v-text-field
            v-model="search"
            label="Search"
            prepend-inner-icon="mdi-magnify"
            variant="outlined"
            hide-details
            single-line
          />
        </v-col>
      </v-row>
      <v-data-table
        :headers="headers"
        :items="items"
        :search="search"
      >
        <template #item.cliente="{ item }">
          {{ item.cliente.apellido }} <span class="bg-red">{{ item.id }}</span>
        </template>

        <template #item.total="{ item }">
          ${{ item.total }}
        </template>

        <template #bottom>
          <div class="text-center pt-2">
            <v-pagination
              v-model="page"
              :length="pageCount"
            />
          </div>
        </template>
      </v-data-table>
    </v-row>
  </v-container>
</template>

<script setup>
  import { ref } from 'vue'

  const search = ref('')
  const headers = [
    {
      title: 'Nombre',
      key: 'nombre',
    },
    {
      title: 'Cliente',
      value: 'cliente',
    },
    {
      title: 'Fecha',
      key: 'date',
    },
    {
      title: 'Total',
      key: 'total',
    },
  ]
  const items = [
    {
      id: 1,
      date: '2023-10-01',
      nombre: 'Juan Pérez',
      cliente: {
        apellido: 'Sánchez',
      },
      total: 100.00,
    },
    {
      id: 2,
      date: '2023-10-02',
      nombre: 'María López',
      cliente: {
        apellido: 'Gómez',
      },
      total: 200.00,
    },
    {
      id: 3,
      date: '2023-10-03',
      nombre: 'Carlos García',
      cliente: {
        apellido: 'Martínez',
      },
      total: 150.00,
    },
  ]
</script>
