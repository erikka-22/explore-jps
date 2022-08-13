<template>
  <p>{{ reversedText }}</p>
  <!-- <p>{{ props.originalText }}</p> -->
</template>

<script>
import { computed } from 'vue';  
export default {
  name: "ReversedText",
  props: {
    originalText: {
      type: String,
      default: ''
    }
  },
  setup(props) {
    const reversedText = computed(
      () => {
        return props.originalText.split('').reverse().join('')
      }
    )
    const log = () => {
      return props.originalText
    }
    return {
      reversedText,
      log
    }
  }
}
</script>

<style>

</style>