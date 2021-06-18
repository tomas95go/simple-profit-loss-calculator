<template>
  <form @submit.prevent>
    <div class="field is-horizontal">
      <div class="field-label is-normal">
        <label class="label">I bought </label>
      </div>
      <div class="field-body">
        <div class="field">
          <p class="control is-expanded">
            <input class="input" type="text" placeholder="quantity acquired" />
          </p>
        </div>
        <div class="field">
          <div class="select">
            <select v-model="selectedVolatile">
              <option disabled value="">Coin</option>
              <option
                v-for="coin in volatileCoins"
                :key="coin.id"
                :value="coin.name"
              >
                {{ coin.name }}
              </option>
            </select>
          </div>
        </div>
        <div class="field-label is-normal">
          <label class="label"> with </label>
        </div>
        <div class="field">
          <p class="control is-expanded">
            <input type="text" class="input" placeholder="invested amount" />
          </p>
        </div>
        <div class="field">
          <div class="select">
            <select v-model="selectedStable">
              <option disabled value="">Coin</option>
              <option
                v-for="coin in stableCoins"
                :key="coin.id"
                :value="coin.name"
              >
                {{ coin.name }}
              </option>
            </select>
          </div>
        </div>
      </div>
    </div>
  </form>
</template>

<script>
export default {
  name: 'DataEntry',
  data() {
    return {
      coinList: [
        {
          id: 1,
          name: 'DOT',
          type: 'volatile',
        },
        {
          id: 2,
          name: 'BUSD',
          type: 'stable',
        },
      ],
      investedAmount: 15,
      quantityAcquired: 9.78,
      selectedVolatile: '',
      selectedStable: '',
    }
  },
  computed: {
    volatileCoins() {
      return this.coinList.filter((coin) => coin.type === 'volatile')
    },
    stableCoins() {
      return this.coinList.filter((coin) => coin.type === 'stable')
    },
  },
}
</script>
