<template>
  <div class="activ-card">
      <span class="top">
      <img class="wifi" src="../assets/wifi.svg" alt="">
      <img class="bitcoin" src="../assets/bitcoin.svg" alt="">
      </span>
      <img class="chip" src="../assets/chip.svg" alt="">
      <p>1234 5678  1234  2343</p>
  </div>
</template>

<script>
export default {
    name: 'activcard',


}
</script>

<style scoped lang="scss">
 .activ-card{
     width: 350px;
     height: 220px;
     background-color: #ffae34;
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
    .chip{
        width: 40px;
        background-color: white;
        border-radius: 5px;
        margin-left: 20px;
    }
    p{
        font-size: 1.5rem;
        text-align: center;
        margin: 5px;
        font-family: "PT Mono", monospace;
        

    }
 }
</style>