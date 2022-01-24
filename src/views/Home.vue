<template>
  <div class="home">
    <header>
      <h1>E-WALLET</h1>
      <p>ACTIV CARD</p>
    </header>
    <main>
        <div class="top-section">
          
          <!-- <SingleCard v-if="card" v-bind:card="card"  /> -->
        </div>
        <div class="middle-section">
            <CardList @viewChange="$emit('viewChange')"/> 
        </div>
    </main>
    <footer>
        <!-- <button class="addbtn" @click="toAddCard">ADD A NEW CARD</button> -->
    </footer>
  </div>
</template>

<script>
// import SingleCard from "../components/SingleCard.vue";
import CardList from "../components/CardList.vue";
export default {
  name: "Home",
  components: {  CardList, },
  props: ['card'],
  data(){return{

  }},
  methods: {
      toAddCard(){
          this.$emit('changePage')
      }
  }
};
</script>

<style scoped lang="scss">
header{
    text-align: center;
}

</style>