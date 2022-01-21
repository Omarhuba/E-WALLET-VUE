<template>
  <div class="home">
    <header>
      <h1>E-WALLET</h1>
      <p>ACTIV CARD</p>
    </header>
    <main>
        <div class="top-section">

          <ActivCard />
        </div>
        <div class="middle-section">
            <CardList/> 
        </div>
    </main>
    <footer>
        <button @click="toAddCard" class="addbtn">ADD A NEW CARD</button>
    </footer>
  </div>
</template>

<script>
import ActivCard from "../components/ActivCard.vue";
import CardList from "../components/CardList.vue";
export default {
  name: "Home",
  components: { ActivCard , CardList},
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
.addbtn{
    width: 350px;
    height: 50px;
    background-color: white;
    border-radius: 10px;
    font-family: "PT Mono", monospace;
    font-size: 1.4rem;
    font-weight: bold;

}
</style>