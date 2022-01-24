<template>
  <div>
      <SingleCard v-if="!formData" :card="card" class="single-card"/>
      <SingleCard   @clicked="changeActiv(index)"
                    :card="card"
                    v-else
                    v-for="(card,index) in formData" :key="card.index"
                    class="grupp-card"
                    />
            <button class="addbtn" v-if="!formData" @click="$emit('viewChange')">ADD A NEW CARD</button>
            <button class="full-addbtn" v-else @click="$emit('viewChange')">ADD A NEW CARD</button>
  </div>
</template>

<script>
import SingleCard from './SingleCard.vue'
export default {
  name: 'cardlist',
  components: {SingleCard},
  mounted() {
    this.formData = JSON.parse(localStorage.getItem("savedCards"));
  },
  data(){return{
    formData: [],
    card: {
      cardNumber: '',
      cardholderName: '',
      year: '',
      month: '',
      valid: '',
      ccv: '',
      vendor: {}
    },
  }},
  methods: {
    changeActiv(index){
      if(index > 0){
        let newActiv = this.formData[index];
        this.formData.splice(index,1)
        this.formData.unshift(newActiv)
      }
    }
  }
}
</script>

<style scoped lang="scss">
 .addbtn{
    width: 350px;
    height: 60px;
    background-color: white;
    border-radius: 10px;
    font-family: "PT Mono", monospace;
    font-size: 1.4rem;
    font-weight: bold;
    margin-top: 50px;

}
.full-addbtn{
  width: 350px;
  height: 60px;
  background-color: white;
  border-radius: 10px;
  font-family: "PT Mono", monospace;
  font-size: 1.4rem;
  font-weight: bold;
  margin-top: 450px;               
}

.grupp-card:nth-child(1){
  position: relative;
}
.grupp-card:nth-child(2){
  position: absolute;
  transform: translateY(25%);
}
.grupp-card:nth-child(3){
  position: absolute;
  transform: translateY(50%);
}
.grupp-card:nth-child(4){
  position: absolute;
  transform: translateY(75%);
}
.grupp-card:nth-child(5){
  position: absolute;
  transform: translateY(100%);
}
</style>