<template>
  <div class="popular-products">
    <h2 class="popular-products-title">
      Productos populares
    </h2>

    <div
      v-for="product in popularProducts"
      :key="product.id"
      class="popular-products__container"
    >
      <div class="popular-products__container-img" />
      <div>
        <p class="popular-products__container-title">
          {{ product.title }}
        </p>
        <span class="popular-products__container-catogory">{{ product.category }}</span>
      </div>
    </div>
  </div>
</template>

<script setup>
import { ref } from 'vue';


const popularProducts = ref([
  {
    id: 1,
    img: '',
    title: 'Limpiador',
    category: 'clean'
  },
  {
    id: 2,
    img: '',
    title: 'Desodorante',
    category: 'clean'
  }
])
</script>

<style lang="scss" scoped>
.popular-products {
  background-color: #212121;
  padding: 18px 15px;
  border-radius: 10px;

  &-title {
    font-size: 25px;
    font-weight: 500;
    margin-bottom: 25px;
  }

  &__container {
    display: flex;
    align-items: center;
    gap: 15px;
    background-color: #3D4142 ;
    padding: 5px;
    margin-bottom: 15px;
    border-radius: 7.43px;

    &-img {
      width: 90px;
      height: 66px;
      border-radius: 10px;
      background-color: #212121;
    }

    &-title {
      font-weight: 500;
      font-size: 16px;
    }

    &-catogory {
      font-size: 14px;
      color: #777979;
    }
  }

}
</style>
