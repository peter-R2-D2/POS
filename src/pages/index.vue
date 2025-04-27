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

    <div
      class="d-flex justify-md-space-between overflow-auto my-6"
    >
      <CardMounted
        v-for="staft in dashboardStaft"
        :key="staft.title"
        :staft="staft"
      />
    </div>

    <v-row>
      <v-col
        cols="12"
        md="6"
      >
        <PopularProducts />
      </v-col>

      <v-col
        cols="12"
        md="6"
      >
        <ProductStock />
      </v-col>
    </v-row>
  </div>
</template>

<script setup>
import CardMounted from '@/components/Dashboard/CardMounted.vue';
import PopularProducts from '@/components/Dashboard/PopularProducts.vue';
import ProductStock from '@/components/Dashboard/ProductStock.vue';

const dashboardStaft = [
  {title: 'Ventas Diarias', value: '20,000', date: '17/04/2025'},
  {title: 'Ingresos Mensuales', value: '20,000', date: '17/04/2025'},
  {title: 'Reservas en el mes', value: '20', date: '17/04/2025'}
]
</script>
