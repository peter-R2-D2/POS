<template>
  <div class="card flex-shrink-0">
    <div>
      <div class="card__container">
        <p class="card__title">
          {{ props.staft.title }}
        </p>
        <p class="card__value">
          {{ props.staft.value }}
        </p>
      </div>
      <p>{{ staft.date }}</p>
    </div>
    <div>
      <v-icon
        class="card__icon rounded-circle"
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

<style lang="scss" scoped>
.card {
  width: 340px;
  background-color: #212121;
  padding: 18px 15px;
  display: flex;
  justify-content: space-between;
  border-radius: 10px;

  @media screen and (max-width: 768px) {
    width: 300px;
    margin-right: 20px;

    &:last-child {
      margin-right: 0;
    }
  }

  &__container {
    margin-bottom: 40px;
  }

  &__title {
    font-family: Poppins, sans-serif;
    font-weight: 300;
    font-size: 16px;
  }

  &__value {
    font-weight: 500;
    font-size: 25px;
  }

  &__date {
    font-weight: 300;
    font-size: 16px;
    color: #777979
  }

  &__icon {
    background-color: #2196F3
  }
}
</style>
