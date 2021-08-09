<template>
  <button class="button is-black" @click="this.$emit('changeLanguage')">
    {{ displayBtnLanguageText }}
  </button>
</template>

<script>
export default {
  name: 'LangBtn',
  props: {
    currentLanguage: String,
  },
  computed: {
    displayBtnLanguageText() {
      let btnLanguageText = ``
      if (this.currentLanguage === 'ENG') {
        btnLanguageText = `Spanish`
      }

      if (this.currentLanguage === `SPA`) {
        btnLanguageText = `Inglés`
      }

      return btnLanguageText
    },
  },
}
</script>
