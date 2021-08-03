<template>
  <div class="content is-flex is-justify-content-center">
    <ul v-show="errorQuantity" class="has-text-justified">
      <li
        class="has-text-warning-dark"
        v-for="error in formErrors"
        :key="error.id"
      >
        {{ error.message }}
      </li>
    </ul>
  </div>
</template>

<script>
export default {
  name: 'ErrorList',
  props: {
    errorQuantity: Number,
    formErrors: Array,
  },
}
</script>
