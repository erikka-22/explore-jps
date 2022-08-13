<template>
  <span>basePrice</span>
  <input type="text" v-model="basePrice"/>
  <p>{{ basePrice }}</p>
</template>

<script>
import { computed } from 'vue';  
export default {
  name: "BasePrice",
  // props: {
  //   basePrice: {
  //     type: Number,
  //     default: 0
  //   }
  // },
  setup() {
    const basePrice = computed({
      get: () => 100
      // set: val => val * 100
    })
    return {
      basePrice,
    }
  }
}
</script>

<style>

</style>