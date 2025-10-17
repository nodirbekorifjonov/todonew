<script setup lang="ts">
import FormCreate from "@/components/FormCreate.vue";
import TasksList from "@/components/TasksList.vue";
import { onMounted, ref, watch } from "vue";

interface Task {
  id: string;
  text: string;
  completed: boolean;
}

const tasks = ref<Task[]>(JSON.parse(localStorage.getItem("tasks") || "[]"));

const handleAddTask = (newTask: Task) => {
  tasks.value.push(newTask);
};

const handleUpdateTask = (updatedTask: Task) => {
  const index = tasks.value.findIndex((t) => t.id === updatedTask.id);
  if (index !== -1) {
    tasks.value[index] = updatedTask;
  }
};

const handleDeleteTask = (taskId: string) => {
  tasks.value = tasks.value.filter((t) => t.id !== taskId);
};

onMounted(() => {
  if (!localStorage.getItem("tasks")) {
    localStorage.setItem("tasks", JSON.stringify([]));
  }
});

watch(
  tasks,
  (newVal) => {
    localStorage.setItem("tasks", JSON.stringify(newVal));
  },
  { deep: true }
);
</script>

<template>
  <main class="pt-[91px]">
    <FormCreate class="absolute top-[172px]" @add-task="handleAddTask" />
    <TasksList
      :tasks="tasks"
      @update-task="handleUpdateTask"
      @delete-task="handleDeleteTask"
    />
  </main>
</template>
<style scoped></style>
