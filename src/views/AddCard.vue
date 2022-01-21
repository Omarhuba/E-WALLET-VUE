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

      <CardForm/>
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
.addcard{
    // width: 600px;
    // height: 1000px;
    // background-color: yellowgreen;
}
}    
</style>