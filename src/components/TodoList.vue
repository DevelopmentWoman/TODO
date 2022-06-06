<template>
    <div class="c-list">
        <ul>
            <todo-item 
            v-for="todo of todos"
            :key="todo.id" 
            :todo = "todo"
            />

            <todo-footer/>
        </ul>
        <todo-filter v-if="screenWidth<768" class="d-filter"/>

    </div>
</template>

<script>
import { inject,computed,ref,provide} from 'vue'
import TodoItem from './TodoItem.vue'
import TodoFooter from './TodoFooter.vue'
import TodoFilter from './TodoFilter.vue'

export default {
    components: { TodoItem, TodoFooter, TodoFilter },
    setup(){
        const todosT = inject("todos")
        const stateF = ref("all")
        const screenWidth = screen.width 
        
        const todos = computed(()=>{
            if(stateF.value==="all"){
                return todosT.value
            }
            if(stateF.value==="act"){
                return todosT.value.filter(elemt => elemt.state === false)
            }
            if(stateF.value==="comp"){
                return todosT.value.filter(elemt => elemt.state === true)
            }

        })


        provide("stateF",stateF)
        return {todos,screenWidth}
    }
}
</script>

<style>

</style>