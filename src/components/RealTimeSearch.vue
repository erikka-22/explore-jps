<template>
  <p>検索キーワード<input type="text" v-model="searchKeyword"></p>
  <p>結果</p>
  <ul id="itemLists">
    <li v-for="item in items" :key="item.id">
      {{ item }}
    </li>
  </ul>
</template>

<script>
import { watch } from 'fs';
import { ref } from 'vue';

export default {
  name: 'RealTimeSearch',
  setup() {
    const searchKeyword = ref('')

    const items = ref([])

    watch(
      () => searchKeyword,
      (tmpKeyword) => {
        
      }
    )

    return {
      searchKeyword,
      items
    }
  }
} 
</script>

<style>

</style>