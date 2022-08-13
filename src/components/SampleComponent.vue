<template>
  <!-- <p>firstName: <input type="text" v-model="state.name.firstName"></p>
  <p>lastName: <input type="text" v-model="state.name.lastName"></p>
  <p>fullname: {{ state.fullName }}</p>
  <p>fullname: {{ compFullName }}</p> -->
  <RealTimeSearch></RealTimeSearch>
</template>
<script>
import { reactive, watch, computed } from 'vue'
import RealTimeSearch from './RealTimeSearch.vue'
// import _ from 'lodash'

export default {
    name: "SampleComponent",
    components: { RealTimeSearch },
    setup() {
        const state = reactive({
            text: "message",
            km: 0,
            m: 0,
            name: {
              firstName: '',
              lastName: '',
              fullName: ''
            }
        })
        // const originalText = 'Hello Vue.js'

        const compFullName = computed(
          () => state.name.firstName + ' ' + state.name.lastName
        )

        // const methodsNumber = () => Math.random()

        watch(
          // () => _.cloneDeep(state),
          () => state,
          (tmpState) => {
            state.fullName = tmpState.name.firstName + ' ' + tmpState.name.lastName
          },
          { deep: true }
        )

        return {
            state,
            compFullName
        };
    }
}
</script>
<style>
  [v-cloak] {
    display: none;
  }
</style>