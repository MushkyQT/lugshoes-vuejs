<template>
  <div class="product-info-colors columns is-mobile mx-3 mb-5 pb-2">
    <div class="column is-flex-mobile is-justify-content-center">
      <label class="color">
        <input type="radio" checked="checked" name="colors" value="green" @click="onColorClick('green')"/>
        <span class="radio--button" id="color-1"></span>
      </label>
    </div>
    <div class="column is-flex-mobile is-justify-content-center">
      <label class="color">
        <input type="radio" name="colors" value="blue" @click="onColorClick('blue')"/>
        <span class="radio--button" id="color-2"></span>
      </label>
    </div>
    <div class="column is-flex-mobile is-justify-content-center">
      <label class="color">
        <input type="radio" name="colors" value="yellow" @click="onColorClick('yellow')"/>
        <span class="radio--button" id="color-3"></span>
      </label>
    </div>
    <div class="column is-flex-mobile is-justify-content-center">
      <label class="color">
        <input type="radio" name="colors" value="red" @click="onColorClick('red')"/>
        <span class="radio--button" id="color-4"></span>
      </label>
    </div>
  </div>
</template>

<script>
export default {
  name: "ProductOptionsColors",
  emits: ['request-shoes-by-color'],
  methods: {
    onColorClick(color) {
      this.$emit('request-shoes-by-color', color)
    }
  }
}
</script>

<style scoped>
.color {
  font-size: 2.5rem;
  cursor: pointer;
}

.radio--button {
  display: block;
  width: 40px;
  height: 40px;
  border-radius: 50%;
}

.product-info-colors input {
  display: none;
}

#color-1 {
  background-color: #65CA8D;
}

#color-2 {
  background-color: #56AEFF;
}

#color-3 {
  background-color: #FFE380;
}

#color-4 {
  background-color: #FF5858;
}

.product-info-colors input:checked + .radio--button {
  background-color: white !important;
}

.product-info-colors input:checked + #color-1 {
  border: 0.25em solid #65CA8D;
}

.product-info-colors input:checked + #color-2 {
  border: 0.25em solid #56AEFF;
}

.product-info-colors input:checked ~ #color-3 {
  border: 0.25em solid #FFE380;
}

.product-info-colors input:checked ~ #color-4 {
  border: 0.25em solid #FF5858;
}
</style>