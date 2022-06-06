<template>
<div class="cont-app">
    <div class="title">
        <h1 class="">TODO</h1>
        <button @click="imgChange"><img src="../../public/imagenes/icon-sun.svg" alt=""></button>
    </div>
    <todo-form />
    <todo-list />

</div>
</template>

<script>
import {provide,ref, watchEffect} from "vue"
import TodoForm from './TodoForm.vue'
import TodoList from './TodoList.vue'



export default {
    components: { TodoForm, TodoList},
    setup(){
        const todos = ref([])
        provide("todos", todos)

        const imgChange = e=>{
            const elem = e.target
            const dadElem = elem.closest('button')
            const elemSelectImg = elem.closest('.container-fluid').previousSibling.firstChild
            const elemSelectBg = elem.closest('.container-fluid').previousSibling.lastChild
            const ul = elem.closest('.cont-app').children[2].firstChild
            const allLi = document.querySelectorAll('.li-item')
            const form = elem.closest('.cont-app').children[1]
            const formInput = elem.closest('.cont-app').children[1].lastChild
            const dFooter = document.querySelector('.filter')


            if(elemSelectImg.classList.contains('bg-img-dark-mobile') | elemSelectImg.classList.contains('bg-img-dark-desktop')) {
                if(screen.width < 768){
                    elemSelectImg.classList.remove('bg-img-dark-mobile')
                    elemSelectImg.classList.add('bg-img-light-mobile')  
                }else{
                    elemSelectImg.classList.remove('bg-img-dark-desktop')
                    elemSelectImg.classList.add('bg-img-light-desktop')  
                }
                elemSelectImg.classList.remove('bg-img-dark')
                elemSelectImg.classList.add('bg-img-light')  

                elemSelectBg.classList.remove('bg-dark')
                elemSelectBg.classList.add('bg-light') 
                dadElem.firstChild.setAttribute('src','/imagenes/icon-moon.svg') 

                form.classList.remove('bg-dark')
                form.classList.add('bg-light')
                formInput.classList.remove('bg-dark')
                formInput.classList.add('bg-light')
                ul.classList.remove('bg-dark')
                ul.classList.add('bg-light')
                allLi.forEach(elem =>{
                     elem.classList.add('color-bg-light')
                     if(elem.classList.contains("color-bg-dark")) elem.classList.remove('color-bg-dark')
                     
                })
                dFooter.classList.remove('bg-dark')
                dFooter.classList.add('bg-light')
            }else{
                if (screen.width < 768){
                    console.log(1)
                    elemSelectImg.classList.remove('bg-img-light-mobile')
                    elemSelectImg.classList.add('bg-img-dark-mobile')
                }else{
                    console.log(2)
                    elemSelectImg.classList.remove('bg-img-light-desktop')
                    elemSelectImg.classList.add('bg-img-dark-desktop')
                }


                elemSelectBg.classList.remove('bg-light') 
                elemSelectBg.classList.add('bg-dark-backg')

                dadElem.firstChild.setAttribute('src','/imagenes/icon-sun.svg')

                form.classList.remove('bg-light')
                form.classList.add('bg-dark')
                formInput.classList.remove('bg-light')
                formInput.classList.add('bg-dark')

                ul.classList.remove('bg-light')
                ul.classList.add('bg-dark')
                allLi.forEach(elem =>{
                     elem.classList.remove('color-bg-light')
                     if(elem.classList.contains("color-bg-light")) elem.classList.add('color-bg-dark')
                })
                dFooter.classList.remove('bg-light')
                dFooter.classList.add('bg-dark')
            }

        }


        if (localStorage.getItem("ToDo")){
            todos.value = JSON.parse(localStorage.getItem("ToDo"))
        }
        watchEffect(()=>{
           localStorage.setItem("ToDo",JSON.stringify(todos.value))
        })

        return {imgChange}
    }



}
</script>


