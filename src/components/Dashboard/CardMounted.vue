<template>
  <div class="d-flex">
    <div>
      <div>
        <p>{{ props.staft.title }}</p>
        <p>{{ props.staft.value }}</p>
      </div>
      <p>{{ staft.date }}</p>
    </div>
    <div>
      <v-icon
        class="bg-red rounded-circle"
        icon="mdi-currency-usd"
      />
    </div>
  </div>
</template>

<script setup>
const props = defineProps({
  staft: {
    type: Object,
    required: true
  }
})
</script>

<style scoped>

</style>
