<template>
      <li 
        class="li-foot-alert" 
        v-if="todos.length===0"
        >
            There isn't ToDos
      </li>
      <li v-else class="li-foot-info">
        <div class="count-items">
          <span role="button"> {{countActive}} items left </span>
          <todo-filter v-if="screenWidth >= 768" class="filter-screen768"/>
          <span role="button" class="clearCompleted" @click="deleteCompleted">
            Clear Completed
          </span>
        </div>
      </li>

</template>

<script>
import TodoFilter from './TodoFilter.vue'
import {inject, computed} from "vue"
export default {
  components: {TodoFilter },
  setup(){
    const todos = inject("todos")
    const screenWidth = screen.width 


    const countActive = computed(()=>{
      return todos.value.filter(elem => elem.state === false).length
    })

    const deleteCompleted = ()=>{
      todos.value = todos.value.filter(elem => elem.state === false)
    }
    return{todos, countActive,deleteCompleted,screenWidth}
  }
}
</script>

<style>

</style>