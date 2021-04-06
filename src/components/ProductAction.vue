<template>
  <span v-html="generateButton(available)"></span>
</template>

<script>
export default {
  name: "ProductAction",
  props: {
    available: Boolean
  },
  data() {
    return {
      buttonHTML: ''
    }
  },
  watch: {
    available: function () {
      this.generateButton(this.available)
    }
  },
  methods: {
    generateButton: function (available) {
      let buttonHTML = ''
      if (available) {
        buttonHTML = '<div class="product-actions"><a href="#" class="add-to-cart" data-value="">Add to cart</a></div>'
      } else {
        buttonHTML = '<div class="product-actions btn-disabled"><a href="#" class="add-to-cart" data-value="">Out of stock</a></div>'
      }
      return buttonHTML
    }
  }
}
</script>

<style scoped>

</style>