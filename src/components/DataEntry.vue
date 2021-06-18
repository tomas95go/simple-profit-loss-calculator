<template>
    <span>
        I bought {{this.quantityAcquired}}
        {{ this.coinList[0].coin }} 
        with {{ this.investedAmount }} 
        {{ this.coinList[1].coin }}
    </span>
</template>

<script>

export default {
  name: "DataEntry",
  data() {
      return {
          coinList: [{
              id: 1,
              coin: 'DOT',
              type: 'volatile'
          },
          {
              id: 2,
              coin: 'BUSD',
              type: 'stable'
          }],
          investedAmount: 15,
          quantityAcquired: 9.78

      }
  }
};
</script>
