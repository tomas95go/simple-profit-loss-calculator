<template>
  <div>
    <h1>Simple profit/loss calculator for Crypto!</h1>
    <p>
      Welcome, this calculator can help you to easily estimate the % of your
      profits or the % of your losses on crypto
    </p>
  </div>
  <div>
    <Card />
  </div>
</template>

<script>
// @ is an alias to /src
import Card from '@/components/Card.vue'

export default {
  name: 'Main',
  components: {
    Card,
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
    }
  },
}
</script>
