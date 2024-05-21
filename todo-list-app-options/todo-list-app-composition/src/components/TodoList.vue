<template>
  <div>
    <h2>Todo list via VueJs</h2>
    <AddTodo @add-todo="addTodo" />
    <ul>
      <TodoItem
        v-for="todo in todos"
        :key="todo.id"
        :todo="todo"
        @remove="removeTodo"
        @complete="completeTodo"
      />
    </ul>
  </div>
</template>

<script>
import AddTodo from '@/components/AddTodo.vue'
import TodoItem from '@/components/TodoItem.vue'
import { ref } from 'vue'

export default {
  components: {
    AddTodo,
    TodoItem
  },
  setup() {
    const todos = ref([])

    const addTodo = (newTodo) => {
      todos.value.push(newTodo)
    }

    const removeTodo = (id) => {
      todos.value = todos.value.filter((todo) => todo.id !== id)
    }
    const completeTodo = (id) => {
      const todo = todos.value.find((todo) => todo.id === id)
      if (todo) {
        todo.complete = true
      }
    }

    return {
      todos,
      addTodo,
      completeTodo,
      removeTodo
    }
  }
}
</script>
