<template>
  <div>
     <SingleCard :card="card"
                 :vendors="vendors"/>
     <br>
     <br>
<form action="user-form" @submit.prevent="submit">
  <label for="card-number">CARD NUMBER</label>
  <input type="number" name="user-name" 
         placeholder="TYPE YOUR CARDNUMBER HERE"
         v-model="card.cardNumber"
         >
  <br>
  <label for="card-name">CARDHOLDER NAME</label>
  <input type="text" name="user-name" placeholder="TYPE YOUR NAME HERE"
         v-model="card.cardholderName"
         >
  <br>
  <div class="valid-thru">
    <span class="year">
      <label for="year">YEAR</label>
      <select name="year" v-model="card.year" class="cardYear">
        <option value="" disabled selected hidden>YYYY</option>
        <option v-for="year in years" :key="year" name="year">
           {{year}} 
        </option>
      </select>
    </span>
    <span class="month">
      <label for="month">MONTH</label>
        <select name="month" v-model="card.month" class="cardMonth" >
          <option value="" disabled selected hidden>MM</option>
         <option v-for="month in months" :key="month" name="month">
          {{month}}
        </option>
      </select>
    </span>

    <!-- <span class="ccv">
      <label for="input">MONTH</label>
      <input type="number" placeholder="MONTH" v-model="card.ccv" min="1" max="12">
    </span> -->

  </div>
<br>
  <label for="vendor">VENDOR</label>
  <select class="vendor" name="vendor" id="vendor" v-model="card.vendor">
     <option value=""  selected hidden>CHOISE YOUR CARD</option>
    <option v-for="vendor in vendors" :key="vendor.vendor" name="vendor"  :value="vendor" v-bind:vendors="vendors">
      {{vendor.name}}
    </option>
  </select>

<br>
 <!-- <button class="addbtn">ADD A NEW CARD</button> -->
 <input class="submit" @click="viewChange" type="submit" value="ADD NEW CARD">
</form>
  </div>
</template>

<script>
import SingleCard from './SingleCard.vue'
export default {
  name: 'cardform',
  components: {SingleCard},
  data(){return{
    formData:[],
    // cards: null ,
    card: {
      cardNumber: '',
      cardholderName: '',
      year: '',
      month: '',
      valid: '',
      ccv: '',
      vendor: {}
    },
    vendors: [{
      name: 'BITCOIN CARD',
      backgroundColor: '#FFAE34',
      color: 'black',
      logo: require('../assets/bitcoin.svg')
    },
    {
      name: 'BLOCKCHAIN CARD',
      backgroundColor: '#8B58F9',
      color: 'white',
      logo: require('../assets/blockchain.svg')
    },
   {
      name: 'NINJA CARD',
      backgroundColor: '#222222',
      color: 'white',
      logo: require('../assets/ninja.svg')
    },
   {
      name: 'EVIL CARD',
      backgroundColor: '#F33355',
      color: 'white',
      logo: require('../assets/evil.svg')
    }],
    years: ['2021','2022','2023','2024','2025','2026'],
    months: ['01','02','03','04','05','06','07','08','09','10','11','12']
  }},
  
  methods: {
    // addCard(){
    //   console.log('add to card.....',this.card)
    //   // this.$emit('send',{...this.card})
    // },
    viewChange(){
      this.$emit('viewChange');
    },
    register(formData){
      console.log(formData)
    },
    
    submit(){
      console.log('submit kann in te funka utan den',this.card)
      // this.$emit('send',{...this.card})
    },
  },
  beforeDestroy() {
    if (localStorage.getItem("savedCards") != undefined) {
      this.formData = JSON.parse(localStorage.getItem("savedCards"));
    }
      this.formData.push(this.card);
      localStorage.setItem("savedCards", JSON.stringify(this.formData)); 
  },

}
</script>

<style scoped lang="scss">
form{
  display: flex;
  flex-direction: column;
}
input{
  width: 350px;
  height: 40px;
  text-align: center;
  border-radius: 20px;
  font-size: 1.1rem;
  border: 1px rgb(20, 196, 250);
  border-color: rgb(83, 158, 151);
  // color: white;
  &:hover{
    background-color: rgb(83, 158, 151);
    transition: 0.5s;
  }
}
.valid-thru{
  display: flex;
  width: 250px;
  .year select{
    width: 170px;
    height: 40px;
    margin-right: 15px;
    border-radius: 20px;
    text-align: center;
    font-size: 1.1rem;
    font-family: "PT Mono", monospace;
    border: 1px rgb(20, 196, 250);
    border-color: rgb(83, 158, 151);
    // color: white;
    &:hover{
      background-color: rgb(83, 158, 151);
      transition: 0.5s;
  }
  }
  .month select{
    width: 170px;
    height: 40px;
    margin-left: 3px;
    border-radius: 20px;
    text-align: center;
    font-size: 1.1rem;
    font-family: "PT Mono", monospace;
    border: 1px rgb(20, 196, 250);
    border-color: rgb(83, 158, 151);
    // color: white;
    &:hover{
      background-color: rgb(83, 158, 151);
      transition: 0.5s;
  }
  }
}
.vendor{
  width: 360px;
  height: 40px;
  text-align: center;
  border-radius: 20px;
  font-size: 1.1rem;
  font-family: "PT Mono", monospace;
  border: 1px rgb(20, 196, 250);
  border-color: rgb(83, 158, 151);
  // color: white;
  &:hover{
    background-color: rgb(83, 158, 151);
    transition: 0.5s;
  }
}
.submit{
  font-weight: 900;
  color: white;
  background-color: black;
  width: 360px;
  height: 60px;
  border: none;
  font-family: "PT Mono", monospace;
}
</style>