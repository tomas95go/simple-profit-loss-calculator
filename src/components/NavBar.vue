<template>
  <nav
    class="navbar"
    :class="isDark"
    role="navigation"
    aria-label="main navigation"
  >
    <div class="navbar-menu">
      <div class="navbar-end">
        <div class="navbar-item">
          <button class="button is-dark" :class="isDark">
            <span class="icon is-small">
              <FontAwesomeIcon :icon="icon" :size="size" :style="style" />
            </span>
          </button>
        </div>
        <div class="navbar-item">
          <LangBtn
            @changeLanguage="this.$emit('changeLanguage')"
            :currentLanguage="currentLanguage"
          />
        </div>
      </div>
    </div>
  </nav>
</template>

<script>
import LangBtn from '@/components/LangBtn.vue'
import { FontAwesomeIcon } from '@fortawesome/vue-fontawesome'
import { faSun } from '@fortawesome/free-solid-svg-icons'
export default {
  name: 'NavBar',
  components: {
    LangBtn,
    FontAwesomeIcon,
  },
  props: {
    currentLanguage: String,
    theme: String,
  },
  data() {
    return {
      icon: faSun,
      size: '2x',
      style: {
        color: 'yellow',
      },
    }
  },
  computed: {
    isDark() {
      return this.theme === `dark` ? 'is-dark' : ''
    },
  },
}
</script>
