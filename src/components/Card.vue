<template>
  <div class="card">
    <header class="card-header">
      <div class="card-header-title is-centered">
        <h3 class="is-size-4 has-text-weight-bold">
          {{ displayTradeCardTitle }}
        </h3>
      </div>
    </header>
    <div class="card-content" v-if="cardRegion === 'data-entry'">
      <DataEntry />
    </div>
  </div>
</template>

<script>
import DataEntry from '@/components/DataEntry.vue'

export default {
  name: 'Card',
  components: {
    DataEntry,
  },
  props: {
    theme: String,
    currentLanguage: String,
  },
  data() {
    return {
      cardRegion: 'data-entry',
      tradeCardTitles: [
        {
          id: 1,
          text: `Input your trade data`,
          language: `ENG`,
        },
        {
          id: 2,
          text: `Ingresa los datos de tu trade`,
          language: `SPA`,
        },
      ],
    }
  },
  computed: {
    displayTradeCardTitle() {
      let currentTitle = this.tradeCardTitles.filter((el) => {
        if (el.language === this.currentLanguage) {
          return el.text
        }
      })

      return currentTitle[0].text
    },
  },
}
</script>
