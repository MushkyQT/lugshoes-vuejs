<template>
  <div v-for="(shoe,index) in shoes" :key="shoe.id" class="column has-text-centered is-flex-mobile"
       :class="calcPosition(index)">
    <li :data-value="shoe.size" :data-id="shoe.id" :class="{disabled: shoe.quantity === 0}"
        @click="requestSpecificShoe(shoe.id), setActive($event.target)">
      <a href="#">{{ shoe.size }}</a>
    </li>
  </div>
</template>

<script>
export default {
  name: "ProductOptionsSizes",
  props: {
    shoes: {
      type: Array,
      required: true
    }
  },
  data() {
    return {
      active: undefined
    }
  },
  emits: ['shoe-updated'],
  methods: {
    calcPosition: function (index) {
      if (index === 0) {
        return ['is-one-third-mobile', 'is-justify-content-flex-end']
      } else if (index === 1) {
        return ['is-one-third-mobile', 'is-justify-content-center']
      } else if (index === 2) {
        return ['is-one-third-mobile', 'is-justify-content-flex-start']
      } else if (index === 3) {
        return ['is-one-half-mobile', 'is-justify-content-flex-end']
      } else if (index === 4) {
        return ['is-one-half-mobile', 'is-justify-content-flex-start']
      }
    },
    requestSpecificShoe: function (id) {
      let self = this
      for (let i = 0; i < self.shoes.length; i++) {
        if (self.shoes[i].id === id) {
          this.$emit('shoe-updated', id)
          return self.shoes[i]
        }
      }
    },
    setActive: function (target) {
      let siblings = target.parentNode.parentNode.children
      siblings.forEach(function (sibling) {
        sibling.firstChild.classList.remove('selected')
      })
      target.classList.add('selected')
    }
  },
  mounted() {
    let self = this
    let target = document.querySelector('li:not(.disabled)')
    if (target) {
      target.classList.add('selected')
      let id = target.dataset.id
      self.requestSpecificShoe(id)
    }
  },
}
</script>

<style scoped>

.product-info-sizes li {
  border: 3px solid var(--primary-color);
  border-radius: 6px;
  font-size: 24px;
  font-weight: 600;
  width: 80px;
  cursor: pointer;
}
</style>