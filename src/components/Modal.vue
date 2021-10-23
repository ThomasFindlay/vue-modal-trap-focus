<script setup>
const props = defineProps({
  isModalOpen: Boolean,
});

onMounted(() => {
  console.log('mounted', props);
});
</script>

<template>
  <div v-if="isModalOpen">Modal</div>
</template>

<style module></style>
