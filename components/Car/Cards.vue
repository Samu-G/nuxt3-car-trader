<script setup>
  import {useCars} from "~/composables/useCars.js";

  const {cars} = useCars();
</script>

<template>
  <div class="w-full">
    <div class="w-full">
      <CarCard v-for="car in cars" :key="car.id" :car="car"/>
    </div>
  </div>
</template>