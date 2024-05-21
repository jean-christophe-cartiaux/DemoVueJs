<template>
  <div class="border">
    <input v-model="newTodo" placeholder="écrivez une nouvelle tâche..." />
    <button @click="handleAddTodo">Ajouter</button>
  </div>
</template>

<script>
import { ref } from 'vue'

export default {
  emits: ['add-todo'],
  setup(props, { emit }) {
    const newTodo = ref('')

    const handleAddTodo = () => {
      if (newTodo.value) {
        emit('add-todo', { id: Date.now(), text: newTodo.value, complete: false })

        newTodo.value = ''
      }
    }
    return {
      newTodo,
      handleAddTodo
    }
  }
}
</script>

<style>
.border{
  border:1px solid red;
  border-radius: 2rem;
}

</style>
