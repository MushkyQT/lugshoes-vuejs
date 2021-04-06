<template>
  <div class="product-info-headline columns is-desktop is-vcentered mb-0 pb-5">
    <div class="column is-flex-mobile is-justify-content-center pb-0">
      <h1>{{ title }}</h1>
    </div>
    <div class="column is-flex-mobile is-justify-content-center">
      <div class="pricetag">{{ price }}&euro;</div>
    </div>
  </div>
</template>

<script>
export default {
  name: "ProductHeadline",
  props: {
    title: String,
    price: Number
  },

}
</script>

<style scoped>
h1 {
  font-weight: 600;
  font-size: 36px;
}

.pricetag {
  padding: 4px 14px;
  border-radius: 6px;
  background-color: var(--primary-color);
  color: white;
  font-weight: 600;
  font-size: 18px;
}
</style>