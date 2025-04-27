<template>
  <div class="overview">
    <div>
      <h2>Overview</h2>

      <div>
        <v-btn />
      </div>
    </div>

    <v-sparkline
      :labels="labels"
      :model-value="value"
      color="blue"
      line-width="1"
      padding="1"
    />
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
  ])
</script>
