<script setup lang="ts">
import { computed } from "vue";

const props = defineProps({
  timeInSeconds: {
    type: Number,
    default: 0,
  },
});

const formattedTime = computed(() =>
  new Date(props.timeInSeconds * 1000).toISOString().substring(11, 19)
);
</script>

<template>
  <section>
    <strong>{{ formattedTime }}</strong>
  </section>
</template>
