<script setup lang="ts">
import { onMounted, ref } from "vue";
import Task from "./Task.vue";
import TasksHeader from "./TasksHeader.vue";

interface Task {
  id: number;
  text: string;
  completed: boolean;
}

const tasks = ref<Task[]>([]);

const updateTask = (updatedTask: Task) => {
  const index = tasks.value.findIndex((t) => t.id === updatedTask.id);
  if (index !== -1) {
    tasks.value[index] = updatedTask;
    localStorage.setItem("tasks", JSON.stringify(tasks.value));
  }
};

onMounted(() => {
  const tasksFromStorage = localStorage.getItem("tasks");
  try {
    tasks.value = tasksFromStorage ? JSON.parse(tasksFromStorage) : [];
  } catch (e) {
    tasks.value = [];
  }
});
</script>

<template>
  <section>
    <div class="site-container">
      <TasksHeader />
      <div class="flex flex-col gap-3 pt-6">
        <Task
          v-for="task in tasks"
          :key="task.id"
          :task="task"
          @update-task="updateTask"
        />
      </div>
    </div>
  </section>
</template>
