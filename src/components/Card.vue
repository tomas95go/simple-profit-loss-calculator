<template>
    <h3> Input your position data </h3>
    <DataEntry />
</template>

<script>

import DataEntry from "@/components/DataEntry.vue";

export default {
  name: "Card",
    components: {
    DataEntry,
  },
};
</script>
