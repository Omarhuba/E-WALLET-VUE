<template>
  <div>
     <SingleCard :card="card"  :vendors="vendors" class="singleCard"/>
<form  @submit.prevent="validate">
  <p v-if="error.length" class="error-text">
    <b>SHOLD BE TYPE YOUR INFO</b>
   <ul>
      <li v-for="e in error" :key="e.id">{{e}}</li>
   </ul>
  </p>
  <label for="card-number">CARD NUMBER</label>
  <input type="text" name="user-name" 
         placeholder="TYPE YOUR CARDNUMBER HERE" 
         onkeypress="return /[0-9, Enter]/i.test(event.key)" minlength="16" maxlength="16"
         pattern="\d*" 
         v-model="card.cardNumber">
  <label for="card-name">CARDHOLDER NAME</label>
  <input type="text" name="user-name" onkeypress="return /[a-ö, ' ', Enter]/i.test(event.key)" maxlength="20"
         placeholder="TYPE YOUR NAME HERE"
         v-model="card.cardholderName">
         <span class="validity"></span>
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
  </div>
  <label for="vendor">VENDOR</label>
  <select class="vendor" name="vendor" id="vendor" v-model="card.vendor">
     <option :value="{}" disabled selected hidden>CHOISE YOUR CARD</option>
    <option v-for="vendor in vendors" :key="vendor.vendor" name="vendor"  :value="vendor" v-bind:vendors="vendors">
      {{vendor.name}}
    </option>
  </select>
 <input class="submit"  type="submit" value="ADD NEW CARD">
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
    error: [],
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
    validate(e){
     if(
       this.card.cardNumber  &&
       this.card.cardholderName  &&
       this.card.year  &&
       this.card.month &&  
       this.card.vendor  
     ){
       console.log('hello to error')
     }
       this.error =[];
      if(!this.card.cardNumber.length ){
        this.error.push('Type Your Card Number')
      }
      if(!this.card.cardholderName.length ){
        this.error.push('Type Your Card HolderName')
      }
      if(!this.card.year.length ){
        this.error.push('Type Your Card Year')
      }
      if(!this.card.month.length ){
        this.error.push('Type Your Card Month')
      }
      if(!Object.keys(this.card.vendor) ){
        this.error.push('Choise Your Card vendor')
      }
        console.warn('error', this.error)
       e.preventDefault()
       if(!this.error.length){
         this.$emit('viewChange');
       }
    },
    viewChange(){
      this.$emit('viewChange');
    },
    register(formData){
      console.log(formData)
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
.singleCard{
  margin-bottom: 30px;
}
input{
  width: 350px;
  height: 40px;
  text-align: center;
  border-radius: 20px;
  font-size: 1.1rem;
  border: 1px rgb(20, 196, 250);
  border-color: rgb(83, 158, 151);
    margin-bottom: 20px;
  &:hover{
    background-color: rgb(83, 158, 151);
    transition: 0.5s;
  }
}
.valid-thru{
  display: flex;
  width: 250px;
  margin-bottom: 20px;
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
  margin-bottom: 20px;
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
.error-text{
  color: red;
  text-align: center;
  font-family: "PT Mono", monospace;
 ul {
  list-style: none;
}
ul li::before {
  content: "😩 👉";
  size: 1rem;
  display: inline-block;
  margin-right: 0.2rem;
}
}
</style>