<template>
  <section>
    <div class="container" v-if="products">
      <ProductView :products="products"/>
    </div>
  </section>
</template>

<script>
import ProductView from "@/components/ProductView";
import axios from "axios";

export default {
  name: 'App',
  components: {
    ProductView
  },
  data() {
    return {
      products: null
    }
  },
  created() {
    let self = this
    axios.get('https://lugus-hiring.frb.io/product').then((response) => {
      self.products = response.data.product
    })
  }
}
</script>

<style>
/* Poppins Font */
@import url('https://fonts.googleapis.com/css2?family=Poppins:wght@100;200;300;400;500;600;700;800;900&display=swap');
/* Bulma */
@import "https://cdn.jsdelivr.net/npm/bulma@0.9.2/css/bulma.min.css";
/* Main stylesheet */
@import "assets/style.css";
/* CSS Resets */
:root {
  --primary-color: #142e2c; /* Lugshoes dark */
}

* {
  box-sizing: border-box;
  -webkit-box-sizing: border-box;
  -moz-box-sizing: border-box;
  margin: 0;
  padding: 0;
}

body {
  font-family: 'Poppins', sans-serif;
  background: #ffffff;
  color: var(--primary-color);
}

a {
  text-decoration: none;
  cursor: default;
  pointer-events: none;
  color: var(--primary-color);
}

ul {
  list-style: none;
}

/* Utils */
.selected {
  background-color: var(--primary-color);
}

.selected a {
  color: white;
}

.disabled {
  opacity: 0.4;
}

.btn-disabled {
  cursor: not-allowed;
}

.btn-disabled .add-to-cart {
  background-color: #d4d4d4;
}

.product-actions {
  display: flex;
  width: 90%;
  max-width: 315px;
  text-align: center;
  margin: 0 auto 40px;
  cursor: pointer;
}

.add-to-cart {
  width: 100%;
  background: #65CA8D;
  border-radius: 30px;
  font-size: 24px;
  font-weight: 600;
  color: white;
  padding: 12px 0;
}
</style>
