<template>
    <li class="li-item">
        <input type="radio" name= "checkBox" class="check-list" :class="{'bg-check': todo.check}"   @click="chec(todo.id,$event)" :for=todo.id>
        <span role="button" @click="availab(todo.id)" class="item-task" :class= "{'text-decoration-line-through': todo.state}"  :id=todo.id> {{todo.text}} </span>
        <span role="button" @click="delet(todo.id)" class="btn-del"> <img src="../../public/imagenes/icon-cross.svg" alt=""> </span>
    </li>
    
</template>

<script>
import {inject} from "vue"

export default {
    props: {
        todo:{
            type: Object,
            required: true
        }
    },
    setup(){
        const todos =  inject("todos")

        const delet = id =>{
            todos.value = todos.value.filter(item=> item.id !== id)
        }

        const chec = (id,event) =>{
            todos.value = todos.value.map(item=> {   
                if(item.id===id){

                    if(!item.state){
                     item.state = true
                     item.check = true

                   
                    }else{
                     item.state = false
                     item.check = false
                    }
                }
                return item
            })
        }

        const availab = id =>{
            todos.value = todos.value.map(item=> {   
                if(item.id===id){
                    item.state = true     
                    item.check = true               
                }
                return item

             });
        }

        return{delet, availab,chec}
        

    }
}
</script>

<style>

</style>