<template>
  <div class="space-y-4">
    <TaskForm @add-task="addTask" />
    <div class="grid grid-cols-1 sm:grid-cols-2 lg:grid-cols-3 gap-4">
      <TaskCard
        v-for="task in tasks"
        :key="task.id"
        :task="task"
        @toggle-complete="toggleComplete"
        @delete-task="deleteTask"
      />
    </div>
  </div>
</template>

<script setup>
import { ref, watch, onMounted } from "vue";
import TaskForm from "./TaskForm.vue";
import TaskCard from "./TaskCard.vue";

const tasks = ref([]);

function loadTasks() {
  const savedTasks = localStorage.getItem("tasks");
  if (savedTasks) {
    tasks.value = JSON.parse(savedTasks);
  }
}

watch(tasks, (newTasks) => {
  localStorage.setItem("tasks", JSON.stringify(newTasks));
}, { deep: true });

onMounted(() => {
  loadTasks();
});

function addTask(task) {
  tasks.value.push({ ...task, id: Date.now(), completed: false });
}

function toggleComplete(id) {
  const task = tasks.value.find((t) => t.id === id);
  if (task) task.completed = !task.completed;
}

function deleteTask(id) {
  tasks.value = tasks.value.filter((t) => t.id !== id);
}
</script>