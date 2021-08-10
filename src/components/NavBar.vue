<template>
  <nav
    class="navbar has-shadow"
    :class="isDark"
    role="navigation"
    aria-label="main navigation"
  >
    <div class="navbar-menu">
      <div class="navbar-end">
        <div class="navbar-item">
          <button
            class="button"
            :class="isDark"
            @click="this.$emit('switchTheme')"
          >
            <span class="icon is-small">
              <FontAwesomeIcon
                :icon="toggleIcon"
                :size="size"
                :style="{ color: isColor }"
              />
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
import { faSun, faMoon } from '@fortawesome/free-solid-svg-icons'
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
      size: '2x',
    }
  },
  computed: {
    isDark() {
      return this.theme === `dark` ? 'is-dark' : 'is-white'
    },
    toggleIcon() {
      return this.theme === `dark` ? faSun : faMoon
    },
    isColor() {
      return this.theme === `dark` ? 'yellow' : 'black'
    },
  },
}
</script>
