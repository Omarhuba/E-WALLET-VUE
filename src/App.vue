<template>
  <div id="app">
    <nav class="navbar">
      <a @click="currentPage = 'home'" href="#">Home</a>
      <a @click="currentPage = 'addcard'" href="#">AddCard</a>
      <a href="#">About Us</a>
      <a href="#">Contact</a>
    </nav>
    <Home v-if="currentPage == 'home'" @changePage="toAddCard" />
    <AddCard v-else-if="currentPage == 'addcard'" />
  </div>
</template>

<script>
import {Home,AddCard} from './views/index'
export default {
  name: 'app',
  components: {Home, AddCard},
  data(){return{
    currentPage: 'home',
    // cards:[
    //   {}
    // ]
  }},
  methods:{
    toAddCard(){
      this.currentPage = 'addcard'
    }
  }


}
</script>

<style lang="scss">
@import url('https://fonts.googleapis.com/css2?family=Source+Sans+Pro:wght@300&display=swap');
* {
  font-family: "PT Mono", monospace;
}
#app{
    width: 450px;
    height: 900px;
    background-color: yellowgreen;
    display: flex;
    flex-direction: column;
    align-items: center;
    margin: auto;
    // text-align: center;
    border-radius: 10px;
    box-shadow: 5px 5px 5px 0px #000000
;

;
}
  .navbar{
    margin: 20px;
    a{
      margin: 10px;
      text-decoration: none;
      color: white;
      font-size: 1.2rem;
      font-weight: 800;
      &:hover{
        color: chocolate;
      }
      
    }
  }
</style>
