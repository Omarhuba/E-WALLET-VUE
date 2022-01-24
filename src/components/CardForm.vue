<template>
  <div>
     <SingleCard :card="card"
               
                  
                  />
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
  <div class="valid-ccv">
    <span class="valid">
      <label for="input">VALID THRU</label>
      <input type="number" placeholder="YYYY/MM"
              v-model="card.valid"   >
    </span>
    <span class="ccv">
      <label for="input">CCV</label>
      <input type="number" placeholder="CCV" v-model="card.ccv" >
    </span>
  </div>
<br>
  <label for="vendor">VENDOR</label>
  <select class="vendor" name="vendor" id="vendor" v-model="card.vendor">
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
      // month: '',
      valid: '',
      ccv: '',
      vendor: {}
    },
    vendors: [{
      name: 'BITCOIN CARD',
      color: '#FFAE34',
      logo: require('../assets/bitcoin.svg')
    },
    {
      name: 'BLOCKCHAIN CARD',
      color: '#8B58F9',
      logo: require('../assets/blockchain.svg')
    },
   {
      name: 'NINJA CARD',
      color: '#222222',
      logo: require('../assets/ninja.svg')
    },
   {
      name: 'EVIL CARD',
      color: '#F33355',
      logo: require('../assets/evil.svg')
    },
   
    ]
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