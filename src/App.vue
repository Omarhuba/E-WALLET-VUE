<template>
  <div id="app">
    <nav class="navbar">
      <a @click="currentPage = 'home'" href="#">Home</a>
      <a @click="currentPage = 'addcard'" href="#">AddCard</a>
      <a href="#">About Us</a>
      <a href="#">Contact</a>
    </nav>
    <Home v-if="currentPage == 'home'" @viewChange="toAddCard" v-bind:card="card" @changePage="changePage"/>
    <AddCard v-else-if="currentPage == 'addcard'"  @viewChange="toAddCard"/>
  </div>
</template>

<script>
import {Home,AddCard} from './views/index'
export default {
  name: 'app',
  components: {Home, AddCard},
  data(){return{
    currentPage: 'home',
    card:null,
    cards: [],
  }},

  methods:{
    changePage(){
      this.currentPage = 'addcard'
    },

    toAddCard(){
      if(this.currentPage == 'home'){
        this.currentPage = 'addcard'
      }else{
        this.currentPage = 'home'
      }
    },
  //   showCard(card){
  //     console.log('this is a app',card)
  //     this.card = card
  //     this.cards.push(this.card)
  //     this.localStorage()
  //   },
  //   localStorage(){
  //     localStorage.setItem('cards', JSON.stringify(this.cards))
  //   }
  // },
  // beforeMount(){
  //   const cards = localStorage.getItem('cards')
  //   if(cards ){
  //     this.cards = JSON.parse(cards)
  //     console.log('this is saved cards', this.cards)
  //   } 
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
  height: 950px;
  background-color: yellowgreen;
  display: flex;
  flex-direction: column;
  align-items: center;
  margin: auto;
  // text-align: center;
  border-radius: 10px;
  box-shadow: 5px 5px 5px 0px #000000;

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
