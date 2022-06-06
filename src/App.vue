<template>
 <div class="container-fluid post-rel" >
    <div class="container-fluid post-abs">
        <div class=" container-fluid bg-img post-abs p-img"></div>
        <div class="container-fluid post-abs bg-dark-backg ps-bg-f"></div>
    </div>
    <div class="container-fluid  post-abs cont-todo">
        <todo-app/>
    </div >

 </div>


</template>

<script>
import TodoApp from './components/TodoApp.vue'
import {onMounted} from 'vue'



export default {
  name: 'App',
  components: {
    TodoApp

  },

setup(){
    onMounted(()=>{
      const bgImg = document.querySelector('.bg-img')
      if (screen.width < 768){
        bgImg.classList.add('bg-img-dark-mobile')
      }else{
        bgImg.classList.add('bg-img-dark-desktop')
      }
    })
  }

  
}
</script>

<style lang='scss' src='./sass/main.scss'>


</style>
