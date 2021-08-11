<template>
  <a
    class="navbar-item"
    :class="[backgroundColor, textColor, isHovered]"
    @click="this.$emit('changeLanguage')"
    @mouseover="hover = true"
    @mouseleave="hover = false"
  >
    {{ displayBtnLanguageText }}
    <img class="pl-2" :src="displayImgSource" />
  </a>
</template>

<script>
export default {
  name: 'LangBtn',
  props: {
    currentLanguage: String,
    theme: String,
  },
  data() {
    return {
      hover: false,
    }
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
    backgroundColor() {
      let backgroundColor = ``
      if (this.theme === `dark`) {
        backgroundColor = `has-background-dark`
      }
      if (this.theme === `light`) {
        backgroundColor = 'has-background-white'
      }
      return backgroundColor
    },
    textColor() {
      let textColor = ``
      if (this.theme === `dark` && this.hover === false) {
        textColor = `has-text-white`
      }
      if (this.theme === `light` && this.hover === false) {
        textColor = `has-text-black`
      }
      return textColor
    },
    isHovered() {
      let isHovered = ``
      if (this.hover) {
        isHovered = `has-text-blue has-text-weight-bold is-underlined`
      }

      if (!this.hover) {
        isHovered = ``
      }
      return isHovered
    },
  },
}
</script>
