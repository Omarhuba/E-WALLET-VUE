<template>
  <div class="home">
    <header>
      <h1>E-WALLET</h1>
      <p>ACTIV CARD</p>
    </header>
    <main>
        <div class="top-section">
        </div>
        <div class="middle-section">
            <CardList @viewChange="$emit('viewChange')"
                      @deletCard="$emit('deletCard')"/> 
        </div>
    </main>
  </div>
</template>

<script>
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
  font-family: "PT Mono", monospace;
}
</style>