<template>
  <div class="product-info-options pb-6">
    <ProductOptionsColors @request-shoes-by-color="passToRoot"/>
    <ul class="product-info-sizes columns is-mobile is-multiline">
      <ProductOptionsSizes @shoe-updated="shoeUpdated" :shoes="matchedShoes" :key="matchedShoes"/>
    </ul>
  </div>
</template>

<script>
import ProductOptionsColors from "@/components/ProductOptionsColors";
import ProductOptionsSizes from "@/components/ProductOptionsSizes";

export default {
  name: "ProductOptions",
  components: {
    ProductOptionsColors,
    ProductOptionsSizes
  },
  props: {
    matchedShoes: {
      type: Object,
      required: true
    }
  },
  emits: ['request-shoes-by-color', 'shoe-updated'],
  methods: {
    passToRoot: function (color) {
      this.$emit('request-shoes-by-color', color)
    },
    shoeUpdated: function (id) {
      this.$emit('shoe-updated', id)
    }
  }
}
</script>

<style scoped>
</style>