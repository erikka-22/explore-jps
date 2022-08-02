<template>
<ul>
  <li v-for="(color, key) in colors" :key="color.id">
    {{ key }} : {{ color.name }}
  </li>
</ul>
<button @click="onClick">Click</button>
<p>{{ now }}</p>
</template>
<script>
// import { ref, reactive } from 'vue'

export default {
  setup () {
    const colors = [
      {
        id: 1,
        name: 'red'
      }, 
      {
        id: 2,
        name: 'blue'
      },
      {
        id: 3,
        name: 'green'
      }
    ]

    const now = '-'
  
    return {
      colors,
      now
    }
  }
}
</script>
<style>
  p {
    color: red;
  }
</style>