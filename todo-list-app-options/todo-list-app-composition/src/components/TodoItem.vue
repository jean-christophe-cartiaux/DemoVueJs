<template>
  <li :style="{ textDecoration: todo.complete ? 'line-through' : 'none' } "class='item-border'>
    {{ todo.text }}
    <button @click="handleRemove" :class="styledList">Supprimer</button>
    <button @click="handleComplete">Terminer</button>
  </li>

  <button @click="switchReactiveClass"> Change le style du button </button>
</template>

<script>
import {reactive, ref} from "vue";

export default {
  props: {
    todo: {
      type: Object,
      required: true
    }
  },
  emit: ['remove', 'complete'],
  setup(props, { emit }) {
    const handleRemove = () => {
      emit('remove', props.todo.id)
    }

    const handleComplete = () => {
      emit('complete', props.todo.id)
    }

    const isValid=ref(true)
    const isError =ref(false)


    const styledList = reactive({
      active:isValid,
      error:isError
    })
    const switchReactiveClass = () => {
      isValid.value= !isValid.value
      isError.value = !isError.value
    }
    return {
      handleRemove,
      handleComplete,
      styledList,
      switchReactiveClass

    }
  }
}
</script>


<style  scoped>
.item-border{
  border:1px solid red;

}
.active{
  background-color :cornflowerblue;
}
.error{
  background-color: chartreuse;
}
</style>