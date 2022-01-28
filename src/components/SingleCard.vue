<template>
  <div @click="$emit('clicked')">
    <article class="activ-card" 
             :card="card"
             :vendors="vendors"
             v-bind:style="cardStyle">
      <div class="top">
        <img class="wifilogo" :src="wifiLogo" />
        <img class="bitcoin" :src="logo"  />
      </div>
      <img class="chip" src="../assets/chip.svg" alt="" />
      <div class="middle" >
        <span>{{ num1 }}</span>
        <span>{{ num2 }}</span>
        <span>{{ num3 }}</span>
        <span>{{ num4 }}</span>
      </div>
      <div class="bottom">
        <div>
          <p>CARDHOLDER NAME</p>
          <p class="cardName">
            {{ fullname }}
          </p>
        </div>
        <div>
          <p>VALID THRU</p>
          <p class="valid">{{ cardYear }}/{{ cardMonth }}</p>
        </div>
      </div>
      <!-- <button class="delete" v-if="deleteBtn"
              @click="$emit('deletCard')">
              DELETE CARD
        <img src="../assets/delete.svg"/>

        </button> -->
    </article>
  </div>
</template>

<script>
export default {
  props: ["card","vendors"],
  data() {return {
    vendorLogo: require('../assets/bitcoin.svg'),
    wifiWhite: require('../assets/wifi_white.svg'),
    wifi: require('../assets/wifi.svg'),
    deleteBtn : true,
    data : {
      firstName: 'FIRSTNAME',
      lastName: 'LASTNAME',
      fullName: '',
    }
  }},
//   mounted(){
//       console.log(this.card, this.vendors)
//   },
  methods: {
    
  },
  computed: {
   
    fullname(){
      let fullname = '';
      if(this.card.cardholderName ){
         fullname = this.card.cardholderName 
      }else{
        fullname = 'FIRSTNAME LASTNAME'
      }
      return fullname
    },
    num1() {
      let num1 = "";
      for (let i = 0; i < 4; i++) {
        if (this.card.cardNumber[i]) {
          num1 += this.card.cardNumber[i];
        } else {
          num1 += "X";
        }
      }
      return num1;
    },
    num2() {
      let num2 = "";
      for (let i = 4; i < 8; i++) {
        if (this.card.cardNumber[i]) {
          num2 += this.card.cardNumber[i];
        } else {
          num2 += "X";
        }
      }
      return num2;
    },
    num3() {
      let num3 = "";
      for (let i = 8; i < 12; i++) {
        if (this.card.cardNumber[i]) {
          num3 += this.card.cardNumber[i];
        } else {
          num3 += "X";
        }
      }
      return num3;
    },
    num4() {
      let num4 = "";
      for (let i = 12; i < 16; i++) {
        if (this.card.cardNumber[i]) {
          num4 += this.card.cardNumber[i];
        } else {
          num4 += "X";
        }
      }
      return num4;
    },
    cardStyle(){
      return{
        color: this.card.vendor.color,
        backgroundColor: this.card.vendor.backgroundColor 
      }
    },
    logo(){
      let logo = '';
      if(this.card.vendor.logo){
        logo = this.card.vendor.logo;
      }else{
        logo = this.vendorLogo
      }
      return logo
    },
    wifiLogo(){
      let wifi= '';
      if(this.card.vendor.name == 'NINJA CARD'){
        wifi = this.wifiWhite
      }else{
        wifi = this.wifi
      }
      return wifi
    },
    cardYear(){
      let year = '';
      if(this.card.year){
        year = this.card.year 
      }else{
          year = 'XXXX'
    }
    return year
    },
    cardMonth(){
      let month = '';
      if(this.card.month){
        month = this.card.month 
      }else{
          month = 'XX'
    }
    return month
    },
  },
};
</script>

<style scoped lang="scss">
.activ-card {
  width: 350px;
  height: 220px;
  background-color: #d0d0d0;
  border: 1px solid black;
  border-radius: 10px;
  box-shadow: 5px 3px 11px -1px rgba(0, 0, 0, 0.84);
  .top {
    display: flex;
    justify-content: space-between;
    margin: 15px 15px 0px 15px;
    .bitcoin {
      width: 60px;
    }
  }
  .middle {
    text-align: center;
    margin: 10px;

    span {
      padding: 10px;
      font-size: 1.5rem;
    }
  }
  .bottom {
    display: flex;
    justify-content: space-around;

    p {
      margin: 10px;
    }
    .cardName {
      margin-bottom: 30px;
      text-transform: uppercase;
    }
  }
  .chip {
    width: 40px;
    background-color: #D0D0D0;
    border-radius: 5px;
    margin-left: 20px;
  }
  .card-number {
    font-size: 1.5rem;
    text-align: center;
    margin: 5px;
    font-family: "PT Mono", monospace;
  }

}
</style>