<template>
  <span>taxIncludedPrice</span>
  <input type="text" :value="inputPrice" />
</template>

<script>
import { computed } from 'vue';  
export default {
  name: "taxIncludedPrice",
  props: {
    taxIncludedPrice: {
      type: Number,
      default: 0
    }
  },
  setup(props) {
    const inputPrice = computed(
      () => {
        return props.taxIncludedPrice
      }
    )
    return {
      inputPrice
    }
  }
}
</script>

<style>

</style>