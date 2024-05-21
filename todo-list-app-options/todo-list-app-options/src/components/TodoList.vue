<template>
  <div>
    <h2>Todo List en VueJs</h2>
    <AddTodo @add-todo="addTodo" />
    <ul>
      <TodoItem
      v-for="todo in todos"
      :key="todo.id"
      :todo="todo"
      @toggle-done="toggleDone"
      @delete-todo="deleteTodo"
      />
    </ul>
  </div>
</template>

<script>
import AddTodo from "@/components/AddTodo.vue";
import TodoItem from "@/components/TodoItem.vue";


export default {
  components:{
    TodoItem,
    AddTodo
  },
  data(){
    return{
      todos:[]
    };
  },
  methods:{
    addTodo(newTodo){
      this.todos.push({id: Date.now(), text: newTodo, done:false})
    },
    deleteTodo(id){
      this.todos=this.todos.filter(todo => todo.id !==id)
    },
    toggleDone(id){
      const todo = this.todos.find(todo => todo.id ===id);
      if (todo){
        todo.done = !todo.done;
      }
    }
  }
}
</script>
