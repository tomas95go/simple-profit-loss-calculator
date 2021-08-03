<template>
  <div>
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
    <div>
      <button @click="validateForm" :value="buttonText">
        {{ buttonText }}
      </button>
    </div>
  </div>
  <ErrorList :formErrors="formErrors" :errorQuantity="errorQuantity" />
</template>

<script>
import ErrorList from '@/components/ErrorList.vue'
export default {
  name: 'DataEntry',
  components: {
    ErrorList,
  },
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
      investedAmount: 0,
      quantityAcquired: 0,
      selectedVolatile: '',
      selectedStable: '',
      buttonText: 'Calculate',
      errorQuantity: 0,
      formErrors: [],
    }
  },
  methods: {
    validateForm() {
      this.formErrors.length = 0
      let errorCode = 0
      let errorMessage = ``
      if (!this.selectedStable) {
        errorCode = 1
        errorMessage = `You need to select a stable coin from the list`
        this.formErrors.push({ id: errorCode, message: errorMessage })
      }

      if (!this.selectedVolatile) {
        errorCode = 2
        errorMessage = `You need to select a volatile coin from the list`
        this.formErrors.push({ id: errorCode, message: errorMessage })
      }

      if (!this.quantityAcquired) {
        errorCode = 3
        errorMessage = `Your quantity acquired must be greater than 0`
        this.formErrors.push({ id: errorCode, message: errorMessage })
      }

      if (!this.investedAmount) {
        errorCode = 4
        errorMessage = `Your invested amount must be greater than 0`
        this.formErrors.push({ id: errorCode, message: errorMessage })
      }

      if (this.formErrors.length) {
        this.errorQuantity = 1
      }

      return this.errorQuantity
    },
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
