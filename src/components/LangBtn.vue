<template>
  <a class="navbar-item" @click="this.$emit('changeLanguage')">
    {{ displayBtnLanguageText }}
    <img class="pl-2" :src="displayImgSource" />
  </a>
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
    displayImgSource() {
      let imgSource = ``
      if (this.currentLanguage === 'ENG') {
        imgSource = `https://i.ibb.co/Z1vc71r/espana-rr.png`
      }

      if (this.currentLanguage === `SPA`) {
        imgSource = `https://i.ibb.co/71hhdR2/reino-unido-rr.png`
      }

      return imgSource
    },
  },
}
</script>
