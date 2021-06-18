<template>
    <h3> Input your position data </h3>
    <div v-if="cardRegion === 'data-entry'">
      <DataEntry />
    </div>
</template>

<script>

import DataEntry from "@/components/DataEntry.vue";

export default {
  name: "Card",
    components: {
    DataEntry,
  },
  data() {
    return {
      cardRegion: 'data-entry',
    }
  }
};
</script>
