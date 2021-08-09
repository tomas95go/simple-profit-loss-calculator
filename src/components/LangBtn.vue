<template>
  <button class="button is-black" @click="this.$emit('changeLanguage')">
    Spanish
  </button>
</template>

<script>
export default {
  name: 'LangBtn',
}
</script>
