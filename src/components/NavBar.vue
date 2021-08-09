<template>
  <nav class="navbar" role="navigation" aria-label="main navigation">
    <div class="navbar-menu">
      <div class="navbar-end">
        <div class="navbar-item">
          <div class="buttons">
            <LangBtn
              @changeLanguage="this.$emit('changeLanguage')"
              :currentLanguage="currentLanguage"
            />
          </div>
        </div>
      </div>
    </div>
  </nav>
</template>

<script>
import LangBtn from '@/components/LangBtn.vue'

export default {
  name: 'NavBar',
  components: {
    LangBtn,
  },
  props: {
    currentLanguage: String,
  },
}
</script>
