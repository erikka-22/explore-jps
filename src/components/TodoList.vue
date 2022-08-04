<template>
  <h1>Todo List</h1>
  <form @submit.prevent>
    <input type="text" v-model="state.newItem">
    <button @click="addItem">add</button>
  </form>
  <ul>
    <li v-for="todo in state.todos" :key="todo.id">
      <input type="checkbox" v-model="todo.isDone">
      <span :class="{ done: todo.isDone }">{{ todo.item }}</span>
      <button @click="deleteItem(todo.id)">Delete</button>
    </li>
  </ul>
</template>

<script>
import { reactive } from 'vue'

export default {
  name: 'TodoList',
  setup() {
    const state = reactive({
      newItem: '',
      todos: [],
      idCounter: 0
    })

    const addItem = () => {
      if (state.newItem === '') {
        return
      }
      const todo = reactive({
        id: state.idCounter,
        item: state.newItem,
        isDone: false
      })

      state.idCounter++
      state.todos.push(todo)
      state.newItem = ''
    }

    const deleteItem = (deleteId) => {
      state.todos = state.todos.filter(todo => todo.id !== deleteId)
    }
    return {
      state,
      addItem,
      deleteItem
    }
  }
}
</script>

<style>
  ul {
    list-style: none;
  }

  .done {
    text-decoration: line-through;
  }
</style>