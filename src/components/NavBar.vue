<template>
  <nav class="navbar" role="navigation" aria-label="main navigation">
    <div class="navbar-menu">
      <div class="navbar-end">
        <div class="navbar-item">
          <div class="buttons">
            <LangBtn @changeLanguage="this.$emit('changeLanguage')" />
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
}
</script>
