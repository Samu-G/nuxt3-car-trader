<script setup>
const props = defineProps({
  description: String,
});
</script>

<template>
  <div class="mt-5 border-b pb-5">
    <p> {{ description }}</p>
  </div>
</template>