<template>
  <NavBar
    @changeLanguage="changeLanguage"
    :currentLanguage="currentLanguage"
    :theme="theme"
    @switchTheme="switchTheme"
  />
  <div>
    <h1>{{ displayTitle }}</h1>
    <p>{{ displayDescription }}</p>
  </div>
  <div>
    <Card :theme="theme" :currentLanguage="currentLanguage" />
  </div>
</template>

<script>
// @ is an alias to /src
import Card from '@/components/Card.vue'
import NavBar from '@/components/NavBar.vue'

export default {
  name: 'Main',
  components: {
    Card,
    NavBar,
  },
  data() {
    return {
      appTitles: [
        {
          id: 1,
          text: `Simple profit/loss calculator for Crypto!`,
          language: `ENG`,
        },
        {
          id: 2,
          text: `Calculadora simple para ganancias/perdidas en Crypto`,
          language: `SPA`,
        },
      ],
      appDescriptions: [
        {
          id: 1,
          text: `Welcome, this calculator can help you to easily estimate the % of your
      profits or the % of your losses on crypto`,
          language: `ENG`,
        },
        {
          id: 2,
          text: `Bienvenido, esta calculadora te ayudara a facilmente estimar el % de tus ganancias o el % de tus perdidas en crypto`,
          language: `SPA`,
        },
      ],
      currentLanguage: ``,
      defaultLanguage: `ENG`,
      title: ``,
      description: ``,
      theme: 'dark',
    }
  },
  methods: {
    changeLanguage() {
      if (this.currentLanguage === `ENG`) {
        this.currentLanguage = `SPA`
      } else {
        this.currentLanguage = `ENG`
      }
      return this.currentLanguage
    },
    changeElementsLanguage() {
      const currentLanguage = this.changeLanguage()
      let currentTitle = ``
      let currentDescription = ``

      if (currentLanguage === `ENG`) {
        currentTitle = this.getTitle(currentLanguage)
        currentDescription = this.getDescription(currentLanguage)
      }

      if (currentLanguage === `SPA`) {
        currentTitle = this.getTitle(currentLanguage)
        currentDescription = this.getDescription(currentLanguage)
      }

      this.title = currentTitle
      this.description = currentDescription
    },
    getTitle(currentLanguage) {
      const title = this.appTitles.filter((el) => {
        if (el.language === currentLanguage) {
          return el
        }
      })
      return title[0].text
    },
    getDescription(currentLanguage) {
      const description = this.appDescriptions.filter((el) => {
        if (el.language === currentLanguage) {
          return el
        }
      })
      return description[0].text
    },
    loadDefaultLanguage() {
      if (this.currentLanguage === ``) {
        this.currentLanguage = this.defaultLanguage
      }
      return this.currentLanguage
    },
    switchTheme() {
      if (this.theme === `dark`) {
        this.theme = `light`
      } else {
        this.theme = `dark`
      }
      return this.theme
    },
  },
  computed: {
    displayTitle() {
      return this.getTitle(this.currentLanguage)
    },
    displayDescription() {
      return this.getDescription(this.currentLanguage)
    },
  },
  created() {
    this.loadDefaultLanguage()
  },
}
</script>
