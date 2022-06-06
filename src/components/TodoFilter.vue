<template>
  <div class="filter">

    <span @click="all($event)" class="actived">All</span>
    <span @click="actives($event)">Active</span>
    <span @click="complete($event)" >Completed</span>
      

  </div>

</template>

<script>
import {inject} from "vue"
export default {

setup(){

    const stateF = inject("stateF")


    const actives = e=>{
        stateF.value = "act"
        if(document.querySelector("ul").classList.contains('bg-light')){
          document.querySelectorAll('li').forEach(element =>{
          element.classList.add('color-bg-light')
          })
        }
        // if(e.target.parentElement.classList.contains('bg-light')){
        //   console.log(document.querySelectorAll('li'))
        //   document.querySelectorAll('li').forEach(element =>{
        //     element.classList.add('color-bg-light')
        //   })
        // }
    }
        const all = e=>{
        stateF.value = "all"
        if(document.querySelector("ul").classList.contains('bg-light')){
          document.querySelectorAll('li').forEach(element =>{
            element.classList.add('color-bg-light')
          })
        }
        // if(e.target.parentElement.classList.contains('bg-light')){
        //   document.querySelectorAll('li').forEach(element =>{
        //     element.classList.add('color-bg-light')
        //   })
        // }
    }
        const complete = e=>{
        stateF.value = "comp"
        if(document.querySelector("ul").classList.contains('bg-light')){
          document.querySelectorAll('li').forEach(element =>{
            element.classList.add('color-bg-light')
          })
        }
        // console.log(e.target.parentElement.classList.contains('bg-light'));
        // if(e.target.parentElement.classList.contains('bg-light')){
        //   console.log(document.querySelectorAll('li'));
        //   document.querySelectorAll('li').forEach(element =>{
        //   element.classList.add('color-bg-light')
        //   })
        // }
    }
    return{actives,all,complete}
}
}
</script>

<style>

</style>