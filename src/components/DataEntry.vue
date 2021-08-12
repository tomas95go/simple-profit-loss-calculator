<template>
  <div class="field is-horizontal">
    <div class="field-label is-normal">
      <label class="label">{{ purchaseText }}</label>
    </div>
    <div class="field-body">
      <div class="field">
        <p class="control is-expanded">
          <input
            class="input"
            type="text"
            placeholder="quantity acquired"
            v-model="quantityAcquired"
            @input="removeError('qtyAcquired')"
          />
        </p>
      </div>
      <div class="field is-narrow">
        <div class="control">
          <div class="select">
            <select
              v-model="selectedVolatile"
              @change="removeError('optionVolatile')"
            >
              <option disabled value="">{{ optionCoinText }}</option>
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
      </div>
    </div>
  </div>
  <div class="field is-horizontal">
    <div class="field-label is-normal">
      <label class="label">{{ purchaseConector }}</label>
    </div>
    <div class="field-body">
      <div class="field">
        <p class="control is-expanded">
          <input
            type="text"
            class="input"
            placeholder="invested amount"
            v-model="investedAmount"
            @input="removeError('investedAmount')"
          />
        </p>
      </div>

      <div class="field is-narrow">
        <div class="control">
          <div class="select">
            <select
              v-model="selectedStable"
              @change="removeError('optionStable')"
            >
              <option disabled value="">{{ optionCoinText }}</option>
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
  </div>
  <div>
    <button class="button" @click="submitForm" :value="buttonText">
      {{ buttonText }}
    </button>
  </div>
  <ErrorList
    :formErrors="formErrors"
    :errorQuantity="errorQuantity"
    :theme="theme"
  />
</template>

<script>
import ErrorList from '@/components/ErrorList.vue'
export default {
  name: 'DataEntry',
  components: {
    ErrorList,
  },
  props: {
    theme: String,
    currentLanguage: String,
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
          name: 'USD',
          type: 'stable',
        },
      ],
      investedAmount: 0,
      quantityAcquired: 0,
      selectedVolatile: '',
      selectedStable: '',
      errorQuantity: 0,
      formErrors: [],
    }
  },
  methods: {
    validateForm() {
      this.formErrors.length = 0
      this.errorQuantity = 0
      let errorCode = 0
      let errorMessage = ``
      let inputError = ``
      if (!this.selectedStable) {
        errorCode = 1
        errorMessage = this.translateError(errorCode)
        inputError = `optionStable`
        this.formErrors.push({
          id: errorCode,
          message: errorMessage,
          errorKey: inputError,
        })
      }

      if (!this.selectedVolatile) {
        errorCode = 2
        errorMessage = this.translateError(errorCode)
        inputError = `optionVolatile`
        this.formErrors.push({
          id: errorCode,
          message: errorMessage,
          errorKey: inputError,
        })
      }

      if (!this.quantityAcquired) {
        errorCode = 3
        errorMessage = this.translateError(errorCode)
        inputError = `qtyAcquired`
        this.formErrors.push({
          id: errorCode,
          message: errorMessage,
          errorKey: inputError,
        })
      }

      if (!this.investedAmount) {
        errorCode = 4
        errorMessage = this.translateError(errorCode)
        inputError = `investedAmount`
        this.formErrors.push({
          id: errorCode,
          message: errorMessage,
          errorKey: inputError,
        })
      }

      if (this.formErrors.length) {
        this.errorQuantity = 1
      }

      return this.errorQuantity
    },
    submitForm() {
      this.validateForm()
    },
    translateError(errorCode) {
      let errorMessage = ``

      if (errorCode === 1 && this.currentLanguage === `ENG`) {
        errorMessage = `You need to select a stable coin from the list`
      }

      if (errorCode === 1 && this.currentLanguage === `SPA`) {
        errorMessage = `Debes seleccionar una moneda estable de la lista`
      }

      if (errorCode === 2 && this.currentLanguage === `ENG`) {
        errorMessage = `You need to select a volatile coin from the list`
      }

      if (errorCode === 2 && this.currentLanguage === `SPA`) {
        errorMessage = `Debes seleccionar una moneda volátil de la lista`
      }

      if (errorCode === 3 && this.currentLanguage === `ENG`) {
        errorMessage = `Your quantity acquired must be greater than 0`
      }

      if (errorCode === 3 && this.currentLanguage === `SPA`) {
        errorMessage = `Tu cantidad adquirida debe ser mayor a 0`
      }

      if (errorCode === 4 && this.currentLanguage === `ENG`) {
        errorMessage = `Your invested amount must be greater than 0`
      }

      if (errorCode === 4 && this.currentLanguage === `SPA`) {
        errorMessage = `El monto de la inversión debe ser mayor a 0`
      }

      return errorMessage
    },
    removeError(errorKey) {
      let errorIndex
      if (this.formErrors.length > 0 && this.quantityAcquired > 0) {
        errorIndex = this.getErrorByIndex(errorKey)
        if (errorIndex !== -1) {
          this.removeErrorByIndex(errorIndex)
        }
      }

      if (this.formErrors.length > 0 && this.investedAmount > 0) {
        errorIndex = this.getErrorByIndex(errorKey)
        if (errorIndex !== -1) {
          this.removeErrorByIndex(errorIndex)
        }
      }

      if (this.formErrors.length > 0 && this.selectedStable !== '') {
        errorIndex = this.getErrorByIndex(errorKey)
        if (errorIndex !== -1) {
          this.removeErrorByIndex(errorIndex)
        }
      }

      if (this.formErrors.length > 0 && this.selectedVolatile !== '') {
        errorIndex = this.getErrorByIndex(errorKey)
        if (errorIndex !== -1) {
          this.removeErrorByIndex(errorIndex)
        }
      }

      return this.formErrors
    },
    getErrorByIndex(errorKey) {
      let index
      index = this.formErrors.findIndex((el) => el.errorKey === errorKey)
      return index
    },
    removeErrorByIndex(index) {
      return this.formErrors.splice(index, 1)
    },
  },
  computed: {
    volatileCoins() {
      return this.coinList.filter((coin) => coin.type === 'volatile')
    },
    stableCoins() {
      return this.coinList.filter((coin) => coin.type === 'stable')
    },
    purchaseText() {
      let purchaseText = ``

      if (this.currentLanguage === `ENG`) {
        purchaseText = `Bought`
      }

      if (this.currentLanguage === `SPA`) {
        purchaseText = `Compré`
      }

      return purchaseText
    },
    purchaseConector() {
      let conector = ``

      if (this.currentLanguage === `ENG`) {
        conector = `With`
      }

      if (this.currentLanguage === `SPA`) {
        conector = `Con`
      }

      return conector
    },
    optionCoinText() {
      let optionCoinText = ``

      if (this.currentLanguage === `ENG`) {
        optionCoinText = `COIN`
      }

      if (this.currentLanguage === `SPA`) {
        optionCoinText = `MONEDA`
      }

      return optionCoinText
    },
    buttonText() {
      let btnText = ``

      if (this.currentLanguage === `ENG`) {
        btnText = `Calculate`
      }

      if (this.currentLanguage === `SPA`) {
        btnText = `Calcular`
      }

      return btnText
    },
  },
}
</script>
