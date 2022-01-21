<template>
  <div>
      <article class="activ-card">
      <div class="top">
          <img class="wifi" src="../assets/wifi.svg" alt="">
          <img class="bitcoin" src="../assets/bitcoin.svg" alt="">
      </div>
          <img class="chip" src="../assets/chip.svg" alt="">
      <div class="middle">
          <!-- <p class="card-number">{{card.cardNumber}}</p> -->
          <span>{{ num1 }}</span>
          <span>{{ num2 }}</span>
          <span>{{ num3 }}</span>
          <span>{{ num4 }}</span>
      </div>
      <div class="bottom">
          <div>
              <p>CARDHOLDER NAME</p>
              <p class="cardName">{{card.cardholderName ? card.cardholderName : 'FIRSTNAME LASTMANE'}}</p>
          </div>
          <div>
              <p>VALID THRU</p>
              <!-- <p class="valid">{{card.valid}}/{{card.valid}}</p> -->
              <p class="valid">{{valid1}}/{{valid2}}</p>

          </div>
      </div>

      </article>
  </div>
</template>

<script>
export default {
    props:['card', 'vendor'],
    data(){return{

    }},
    computed: {
        num1() {
            let span = '';
            for(let i = 0; i < 4; i++){
                if(this.card.cardNumber[i]){
                    span += this.card.cardNumber[i];
                }else{
                    span += 'X';
                }
            }
        return span;
        },
        num2() {
            let span = '';
            for(let i = 4; i < 8; i++){
                if(this.card.cardNumber[i]){
                    span += this.card.cardNumber[i];
                }else{
                    span += 'X';
                }
            }
        return span;
        },
        num3() {
            let span = '';
            for(let i = 8; i < 12; i++){
                if(this.card.cardNumber[i]){
                    span += this.card.cardNumber[i];
                }else{
                    span += 'X';
                }
            }
        return span;
        },
        num4() {
            let span = '';
            for(let i = 12; i < 16; i++){
                if(this.card.cardNumber[i]){
                    span += this.card.cardNumber[i];
                }else{
                    span += 'X';
                }
            }
        return span;
        },
        valid1(){
            let p = '';
            for(let i = 0; i < 4; i++){
                if(this.card.valid[i]){
                    p += this.card.valid[i]
                }else{
                    p += 'X';
                }
            }
            return p;
        },
        valid2(){
            let p = '';
            for(let i = 4; i < 6; i++){
                if(this.card.valid[i]){
                    p += this.card.valid[i]
                }else{
                    p += 'X';
                }
            }
            return p;
        }
    }
}
</script>

<style scoped lang="scss">
 .activ-card{
     width: 350px;
     height: 220px;
     background-color: #D0D0D0;
     border: 1px solid black;
     border-radius: 10px;
     box-shadow: 5px 3px 11px -1px rgba(0,0,0,0.84);
     .top{
         display: flex;
         justify-content: space-between;
         margin: 15px 15px 0px 15px;
         .bitcoin{
             width: 50px;
         }
     }
     .middle{
       text-align: center; 
       margin: 10px;
       span{
           padding: 10px;
           font-size: 1.5rem;
       }    
    }
    .bottom{
        display: flex;
        justify-content: space-around;
        p{
            margin: 10px;

        }
        .cardName{
            margin-bottom: 30px;
        }
    }   
    .chip{
        width: 40px;
        background-color: white;
        border-radius: 5px;
        margin-left: 20px;
    }
    .card-number{
        font-size: 1.5rem;
        text-align: center;
        margin: 5px;
        font-family: "PT Mono", monospace;
    }

 }
</style>