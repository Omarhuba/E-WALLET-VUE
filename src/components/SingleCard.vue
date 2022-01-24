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
        <!-- <p class="card-number">{{card.cardNumber}}</p> -->
        <span>{{ num1 }}</span>
        <span>{{ num2 }}</span>
        <span>{{ num3 }}</span>
        <span>{{ num4 }}</span>
      </div>
      <div class="bottom">
        <div>
          <p>CARDHOLDER NAME</p>
          <p class="cardName">
            {{
              card.cardholderName ? card.cardholderName : "FIRSTNAME LASTMANE"
            }}
          </p>
        </div>
        <div>
          <p>VALID THRU</p>
          <!-- <p class="valid">{{card.valid}}/{{card.valid}}</p> -->
          <p class="valid">{{ valid1 }}/{{ valid2 }}</p>
        </div>
      </div>
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

  }},
//   mounted(){
//       console.log(this.card, this.vendors)
//   },
  methods: {
    
  },
  computed: {
    num1() {
      let span = "";
      for (let i = 0; i < 4; i++) {
        if (this.card.cardNumber[i]) {
          span += this.card.cardNumber[i];
        } else {
          span += "X";
        }
      }
      return span;
    },
    num2() {
      let span = "";
      for (let i = 4; i < 8; i++) {
        if (this.card.cardNumber[i]) {
          span += this.card.cardNumber[i];
        } else {
          span += "X";
        }
      }
      return span;
    },
    num3() {
      let span = "";
      for (let i = 8; i < 12; i++) {
        if (this.card.cardNumber[i]) {
          span += this.card.cardNumber[i];
        } else {
          span += "X";
        }
      }
      return span;
    },
    num4() {
      let span = "";
      for (let i = 12; i < 16; i++) {
        if (this.card.cardNumber[i]) {
          span += this.card.cardNumber[i];
        } else {
          span += "X";
        }
      }
      return span;
    },
    valid1() {
      let p = "";
      for (let i = 0; i < 4; i++) {
        if (this.card.valid[i]) {
          p += this.card.valid[i];
        } else {
          p += "X";
        }
      }
      return p;
    },
    valid2() {
      let p = "";
      for (let i = 4; i < 6; i++) {
        if (this.card.valid[i]) {
          p += this.card.valid[i];
        } else {
          p += "X";
        }
      }
      return p;
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
    }
    // bitcoin(){
    //   let span = '';
    //   if(this.card.vendor.name == 'BITCOIN CARD'){
    //     span = 
    //   }
    // }
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
//   color: 000;
  .top {
    display: flex;
    justify-content: space-between;
    margin: 15px 15px 0px 15px;
    .bitcoin {
      width: 50px;
    //   display: none;
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
  // #wifiLogo{
  //   color: white;
  // }
  .card-number {
    font-size: 1.5rem;
    text-align: center;
    margin: 5px;
    font-family: "PT Mono", monospace;
  }
}
</style>