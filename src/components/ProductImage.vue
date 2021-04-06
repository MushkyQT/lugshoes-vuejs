<template>
  <div class="product-image column mx-6 mt-5 pb-2">
    <img :src="img" alt="Lugshoes">
  </div>
</template>

<script>
export default {
  name: "ProductImage",
  props: {
    color: String
  },
  data() {
    return {
      img: 'https://lugus-hiring.frb.io/storage/shoes-green.png'
    }
  },
  computed: {
    setImageColor: function () {
      let self = this
      self.img = 'https://lugus-hiring.frb.io/storage/shoes-' + self.color + '.png'
      return self.img
    }
  }
}
</script>

<style scoped>

</style>