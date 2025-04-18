<template>
  <div>
    <v-row class="mt-12">
      <v-col
        cols="12"
      >
        <v-card>
          <v-card-title>Dashboard</v-card-title>
          <v-card-text>
            Bienvenido al sistema de gestión de ventas y egresos. Aquí puedes gestionar las ventas, el inventario y los egresos de tu negocio.
          </v-card-text>
        </v-card>
      </v-col>
    </v-row>

    <v-row>
      <v-col
        v-for="staft in dashboardStaft"
        :key="staft.title"
        cols="4"
      >
        <CardMounted :staft="staft" />
      </v-col>
    </v-row>
  </div>
</template>

<script setup>
import CardMounted from '@/components/Dashboard/CardMounted.vue';

const dashboardStaft = [
  {title: 'Ventas Diarias', value: '20,000', date: '17/04.2025'},
  {title: 'Ingresos Mensuales', value: '20,000', date: '17/04.2025'},
  {title: 'Reservas en el mes', value: '20', date: '17/04.2025'}
]
</script>
