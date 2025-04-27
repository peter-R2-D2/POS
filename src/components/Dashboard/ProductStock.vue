<template>
  <div class="products-stock">
    <h2 class="products-stock-title">
      Productos con poco stock
    </h2>

    <div
      v-for="product in productStock"
      :key="product.id"
      class="products-stock__container"
    >
      <div class="products-stock__container-img" />

      <div class="d-flex justify-space-between align-center w-100">
        <div>
          <p class="products-stock__container-title">
            {{ product.title }}
          </p>
          <span class="products-stock__container-catogory">{{ product.category }}</span>
        </div>
        <div
          :class="{
            'out-of-stock': product.stock === 0,
            'in-stock': product.stock > 0
          }"
        >
          {{ product.stock === 0 ? 'Sin stock' : `En stock ${product.stock}` }}
        </div>
      </div>
    </div>
  </div>
</template>

<script setup>

const productStock = [
  {
    id: 1,
    title: "Cars Clean",
    category: "Clean",
    stock: 2
  },
  {
    id: 2,
    title: "Cars Clean",
    category: "Clean",
    stock: 0
  }
]
</script>

<style lang="scss">
.products-stock {
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

.in-stock {
  color: #FAC1D9;
  font-size: 16px;
}

.out-of-stock {
  color: #F60000;
  font-size: 16px;
}
</style>
