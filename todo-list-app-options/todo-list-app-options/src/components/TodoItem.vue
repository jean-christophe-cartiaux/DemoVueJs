<template>
  <li>
    <span :style="{ textDecoration: todo.done ? 'line-through' : 'none' }">
      {{ todo.text }}
    </span>
    <button @click="toggleDone">{{ todo.done ? 'Undo' : 'Terminé' }}</button>
    <button @click="deleteTodo">Supprimer la tâche</button>
  </li>
</template>

<script>
export default {
  props: {
    todo: Object
  },
  methods: {
    toggleDone() {
      this.$emit('toggle-done', this.todo.id)
    },
    deleteTodo() {
      this.$emit('delete-todo', this.todo.id)
    }
  }
}
</script>
