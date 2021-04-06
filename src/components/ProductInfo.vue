<template>
  <p class="product-info-description mx-3 pl-3">
    {{ description }}
  </p>
</template>

<script>
export default {
  name: "ProductInfo",
  props: {
    description: String
  }
}
</script>

<style scoped>
.product-info-description {
  font-size: 14px;
  font-weight: 400;
}
</style>