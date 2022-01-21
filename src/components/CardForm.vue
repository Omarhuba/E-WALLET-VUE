<template>
  <div>
     <SingleCard :card="card"
                  @send="register"/>
     <br>
     <br>


<form action="user-form" @submit.prevent="addCard">
  <label for="card-number">CARD NUMBER</label>
  <input type="text" name="user-name" 
         placeholder="Type your card number here"
         v-model="card.cardNumber"
         >
  <br>
  <label for="card-name">CARDHOLDER NAME</label>
  <input type="text" name="user-name" placeholder="Type your name here"
         v-model="card.cardholderName"
         >
  <br>
  <div class="valid-ccv">
    <span class="valid">
      <label for="input">VALID THRU</label>
      <input type="text" placeholder="yyyy/mm"
              v-model="card.valid"   >
    </span>
    <span class="ccv">
      <label for="input">CCV</label>
      <input type="text" placeholder="ccv" v-model="card.ccv" >
    </span>
  </div>
<br>
  <label for="vendor">VENDOR</label>
  <select class="vendor" name="vendor" id="vendor" v-model="card.vendor">
    <option v-for="vendor in vendors" :key="vendor.vendor" name="vendor">
      {{vendor.name}}
    </option>
  </select>

<br>
 <!-- <button class="addbtn">ADD A NEW CARD</button> -->
 <input class="submit" type="submit" value="ADD NEW CARD">
</form>
  </div>
</template>

<script>
import SingleCard from './SingleCard.vue'
export default {
  name: 'cardform',
  components: {SingleCard},
  data(){return{
    card: {
      cardNumber: '',
      cardholderName: '',
      // month: '',
      valid: '',
      ccv: '',
      vendor: ''
    },
    vendors: [{
      name: 'BITCOIN CARD',
      color: 'yellow',
      logo: require('../assets/bitcoin.svg')
    },
    {
      name: 'BLOCKCHAIN CARD',
      color: 'purple',
      logo: require('../assets/blockchain.svg')
    },
   {
      name: 'NINJA CARD',
      color: 'black',
      logo: require('../assets/ninja.svg')
    },
   {
      name: 'EVIL CARD',
      color: 'red',
      logo: require('../assets/evil.svg')
    },
   
    ]
  }},
  methods: {
    addCard(){
      console.log('asdasd')
    },
    register(formData){
      console.log(formData)
    },
    submit(){
      this.$emit('send',{...this.card})
    }
  }
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
  border-radius: 10px;
  font-size: 1.1rem;
}
.valid-ccv{
  display: flex;
}
.valid{
  margin-right: 3px;
  input{
    flex-direction: row;
    display: flex;
    width: 170px;
    height: 40px;
    
  }
}  
.ccv{
  margin-left: 3px;
  input{
    flex-direction: row;
    display: flex;
    width: 170px;
    height: 40px;
    
  }
}
.vendor{
  width: 360px;
  height: 40px;
  text-align: center;
  border-radius: 10px;
  font-size: 1.1rem;
}
.submit{
  font-weight: 900;
  color: grey;
}
</style>