<template>
  <div
    :class="[ 'p-4 border rounded shadow', task.completed ? 'bg-green-100' : 'bg-white' ]"
  >
    <h3 class="text-lg font-bold">{{ task.title }}</h3>
    <div class="mt-2 flex justify-between items-center">
      <button
        @click="toggleComplete"
        :class="[ 'py-1 px-4 rounded', task.completed ? 'bg-green-500 text-white' : 'bg-gray-200' ]"
      >
        {{ task.completed ? 'Completed' : 'Complete' }}
      </button>
      <button
        @click="deleteTask"
        class="bg-red-500 text-white py-1 px-4 rounded"
      >
        Delete
      </button>
    </div>
  </div>
</template>

<script setup>
import { defineProps, defineEmits } from "vue";

defineProps(["task"]);

const emit = defineEmits(["toggle-complete", "delete-task"]);

function toggleComplete() {
  emit("toggle-complete", task.id);
}

function deleteTask() {
  emit("delete-task", task.id);
}
</script>
