<template>
  <form @submit.prevent="handleSubmit" class="space-y-2">
    <input
      v-model="title"
      type="text"
      placeholder="Add a new task"
      class="w-full p-2 border border-gray-300 rounded"
      required
    />
    <button
      type="submit"
      class="w-full bg-blue-500 text-white py-2 rounded hover:bg-blue-600"
    >
    Adicionar Tarefa
    </button>
  </form>
</template>

<script setup>
import { ref, defineEmits } from "vue";

const title = ref("");

const emit = defineEmits(["add-task"]);

function handleSubmit() {
  if (title.value.trim() !== "") {
    emit("add-task", { title: title.value.trim() });
    title.value = ""; 
  }
}
</script>
