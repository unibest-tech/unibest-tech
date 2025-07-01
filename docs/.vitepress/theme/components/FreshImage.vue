<template>
  <img :src="freshUrl" :alt="alt" width="300" />
</template>

<script setup>
import { computed } from 'vue';
const props = defineProps({
  src: {
    type: String,
    required: true,
  },
  alt: {
    type: String,
    default: '',
  },
});

const freshUrl = computed(() => {
  return `${props.src}?t=${Date.now()}`;
});
</script>
