<template>
  <p>{{ state.text }}</p>
  <p>{{ state.number + 1 }}</p>
  <p>{{ state.text.split('').reverse().join('') }}</p>
  <p>{{ state.bool ? 'YES' : 'NO' }}</p>

  <!-- <p>{{ const x = 1 }}</p> -->
  <p>{{ state.bool ? state.text : '' }}</p>
</template>
<script>
import { reactive } from 'vue'

export default {
    name: "SampleComponent",
    setup() {
      const state = reactive({
        text: "message",
        number: 0,
        bool: false
      });

      return {
        state
      };
    },
}
</script>
<style>
  [v-cloak] {
    display: none;
  }
</style>