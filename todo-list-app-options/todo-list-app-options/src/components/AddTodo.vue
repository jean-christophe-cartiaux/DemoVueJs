<template>
  <div>
    <input v-model="newTodo" placeholder="Ajouter une nouvelle tâche" />
    <button @click="addTodo">Ajouter</button>
  </div>
</template>

<script>
export default {
  data() {
    return {
      newTodo: ''
    }
  },
  methods: {
    addTodo() {
      if (this.newTodo.trim()) {
        this.$emit('add-todo', this.newTodo)
        this.newTodo = ''
      }
    }
  }
}
</script>
