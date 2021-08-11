<template>
  <div class="card">
    <header class="card-header">
      <div class="card-header-title is-centered">
        <h3 class="is-size-4 has-text-weight-bold">Input your position data</h3>
      </div>
    </header>
    <div class="card-content" v-if="cardRegion === 'data-entry'">
      <DataEntry />
    </div>
  </div>
</template>

<script>
import DataEntry from '@/components/DataEntry.vue'

export default {
  name: 'Card',
  components: {
    DataEntry,
  },
  data() {
    return {
      cardRegion: 'data-entry',
    }
  },
}
</script>
