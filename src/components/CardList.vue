<template>
  <div>
      <SingleCard v-if="!formData" :card="card" class="single-card"/>

      <SingleCard   @clicked="changeActiv(index)"
                    :card="card"
                    v-else
                    v-for="(card,index) in formData" :key="card.index"
                    class="grupp-card"
                    @deletCard="$emit('deletCard')"/>

            <!-- <button class="delete" 
            v-if="formData"
              @click="removeCard">
              DELETE CARD
        <img src="../assets/delete.svg"/>

        </button> -->

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
    // avtivCardIndex : 0,
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
    //   this.avtivCardIndex = index
    // },
    // removeCard(){
    //    this.formData.splice(this.avtivCardIndex,1)
    //    localStorage.setItem('savedCards', JSON.stringify(this.formData))
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
    position: fixed;
}
.full-addbtn{
  position: fixed;
  width: 350px;
  height: 60px;
  background-color: white;
  border-radius: 10px;
  font-family: "PT Mono", monospace;
  font-size: 1.4rem;
  font-weight: bold;
  margin-top: 220px;               
}
.grupp-card{
  margin: 10px;
}
.grupp-card:nth-child(1){
  position: relative;
}
.grupp-card:nth-child(2){
  position: absolute;
  transform: translateY(25%);
  &:hover{
    transform: translateY(15%);
  }
}
.grupp-card:nth-child(3){
  position: absolute;
  transform: translateY(50%);
  &:hover{
    transform: translateY(40%);
  }
}
.grupp-card:nth-child(4){
  position: absolute;
  transform: translateY(75%);
  &:hover{
    transform: translateY(65%);
  }
}
.grupp-card:nth-child(5){
  position: absolute;
  transform: translateY(100%);
  &:hover{
    transform: translateY(90%);
  }
}
.grupp-card:nth-child(6){
  position: absolute;
  transform: translateY(125%);
  &:hover{
    transform: translateY(115%);
  }
}
.grupp-card:nth-child(7){
  position: absolute;
  transform: translateY(150%);
  &:hover{
    transform: translateY(140%);
    }
  }
.grupp-card:nth-child(8){
  position: absolute;
  transform: translateY(175%);
  &:hover{
    transform: translateY(165%);
    }
  }
.grupp-card:nth-child(9){
  position: absolute;
  transform: translateY(200%);
  &:hover{
    transform: translateY(190%);
    }
  }
.grupp-card:nth-child(10){
  position: absolute;
  transform: translateY(225%);
  &:hover{
    transform: translateY(215%);
  }
}
</style>