<script setup lang="ts">
  const error = useError();

  const handleError = () => {
    clearError({
      redirect: "/",
    })
  }
</script>

<template>
  <div class="flex h-screen justify-center items-center flex-col">
    <h1 class="text-6xl font-mono">{{ error.statusCode }}</h1>
    <p class="text-3xl m-8 font-mono">{{ error.message }}</p>

    <div class="hover:text-white">
      <NuxtLink class="text-gray-700 hover:text-white font-mono font-bold" @click="handleError">
    <button class="m-8 pl-8 pr-8 pt-2 pb-2 rounded-full bg-cyan-400 hover:bg-sky-500">
        GO BACK
    </button>
      </NuxtLink>
    </div>

  </div>
</template>

