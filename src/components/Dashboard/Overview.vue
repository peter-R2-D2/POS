<template>
  <div class="overview">
    <div>
      <h2 class="overview-title">
        Overview
      </h2>

      <div>
        <v-btn title="Exportar" />
      </div>
    </div>

    <div class="w-100">
      <v-sparkline
        :labels="labels"
        :model-value="value"
        label-size="3"
        color="blue"
        line-width="1"
        padding="8"
      />
    </div>
  </div>
</template>

<script setup>
import { ref } from 'vue';

const labels = ref([
  'Enero',
  'Febrero',
  'Marzo',
  'Abril',
  'Mayo',
  'Junio',
  'Julio',
  'Agosto',
  'Septiembre',
  'Octubre',
  'Noviembre',
  'Diciembre'
])

const value = ref([
    200,
    675,
    410,
    390,
    310,
    460,
    250,
    240,
    310,
    460,
    250,
    240,
  ])
</script>

<style lang="scss">
.overview {
  background-color: #212121;
  border-radius: 10px;
  padding: 25px 16px 40px;
  margin: 24px 0;
}
</style>
