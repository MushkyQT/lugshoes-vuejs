<template>
  <div class="columns is-desktop">
    <ProductImage :color="color"/>
    <div class="product-info column">
      <ProductHeadline :title="products.title" :price="shoePrice"/>
      <ProductOptions @shoe-updated="updateShoes" @request-shoes-by-color="requestShoesByColor"
                      :matchedShoes="matchedShoes"/>
      <ProductInfo :description="products.description"/>
    </div>
  </div>
  <ProductAction :available="shoeAvailable"/>
</template>

<script>
import ProductImage from "@/components/ProductImage";
import ProductHeadline from "@/components/ProductHeadline";
import ProductOptions from "@/components/ProductOptions";
import ProductInfo from "@/components/ProductInfo";
import ProductAction from "@/components/ProductAction";

export default {
  name: "ProductView",
  components: {
    ProductImage,
    ProductHeadline,
    ProductOptions,
    ProductInfo,
    ProductAction
  },
  props: {
    products: {
      type: Object,
      required: true
    }
  },
  data() {
    return {
      color: 'green',
      size: 42,
      matchedShoes: [],
      shoePrice: 120,
      shoeAvailable: true
    }
  },
  methods: {
    requestShoesByColor: function (color) {
      let self = this
      self.matchedShoes = []
      self.products.variants.forEach(function (variant) {
        if (variant.color === color) {
          self.matchedShoes.push(variant)
        }
      })
      self.color = color
      return self.matchedShoes
    },
    updateShoes: function (id) {
      let self = this
      let prods = self.products.variants
      for (let i = 0; i < prods.length; i++) {
        if (prods[i].id == id) {
          self.shoePrice = parseInt(prods[i].price)
          if (prods[i].quantity == 0) {
            self.shoeAvailable = false
          } else {
            self.shoeAvailable = true
          }
        }
      }
    }
  },
  mounted() {
    this.requestShoesByColor(this.color)
  }
}
</script>

<style scoped>

</style>