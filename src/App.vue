<script setup lang="ts">
import Home from "./Home.vue";
</script>

<template>
  <div class="h-screen bg-gray-50 text-gray-800 flex flex-col">
    <header class="p-4 bg-blue-600 text-white text-center text-2xl font-bold">
      Gerenciador de tarefas
    </header>
    <main class="flex-1 p-4">
      <Home />
    </main>
  </div>
</template>
