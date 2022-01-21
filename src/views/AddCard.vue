<template>
  <div class="addcard">
      <header>
        <h1>ADD A NEW BANK CARD</h1>
        <p>NEW CARD</p>
      </header>
      <main>
          <div class="top">
          </div>
          <br>
          <br>
          <div class="middle">
           <CardForm  @send="send" />
          </div>
      </main>
      <br>
      <br>
      <footer>
      </footer>
  </div>
</template>

<script>
import CardForm from '../components/CardForm.vue'
// import SingleCard from '../components/SingleCard.vue'
export default {
    name: 'addcard',
    components: {CardForm, },
    data(){return{

    }},
    methods: {
        addCard(send){
      console.log(send)
    },
    send(card){
        console.log('this is add card component',card) 
         this.$emit('send',{...card})
    }
    }



}
</script>

<style scoped lang="scss">
html,body {
    height: 100%;
}
header{
    width: 350px;
     h1,p{
         width: 200px;
        text-align: center;
        margin: auto;
    }

}    
</style>