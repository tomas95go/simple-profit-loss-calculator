<template>
  <div class="card">
    <header class="card-header" :class="hasBackgroundColor">
      <div class="card-header-title is-centered">
        <h3 class="is-size-4 has-text-weight-bold" :class="hasTextColor">
          {{ displayTradeCardTitle }}
        </h3>
      </div>
    </header>
    <div
      class="card-content"
      :class="contentBackgroundColor"
      v-if="cardRegion === 'data-entry'"
    >
      <DataEntry :currentLanguage="currentLanguage" :theme="theme" />
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
    hasBackgroundColor() {
      let backgroundColor = ``

      if (this.theme === `dark`) {
        backgroundColor = `has-background-dark`
      }

      if (this.theme === `light`) {
        backgroundColor = `has-background-white-ter`
      }

      return backgroundColor
    },
    hasTextColor() {
      let textColor = ``

      if (this.theme === `dark`) {
        textColor = `has-text-white`
      }

      if (this.theme === `light`) {
        textColor = `has-text-grey-dark`
      }

      return textColor
    },
    contentBackgroundColor() {
      let backgroundColor = ``

      if (this.theme === `dark`) {
        backgroundColor = `has-background-grey-dark`
      }

      if (this.theme === `light`) {
        backgroundColor = `has-background-white`
      }

      return backgroundColor
    },
  },
}
</script>
