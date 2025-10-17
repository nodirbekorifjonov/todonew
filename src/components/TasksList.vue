<script setup lang="ts">
import Task from "./Task.vue";
import TasksHeader from "./TasksHeader.vue";

interface TaskType {
  id: string;
  text: string;
  completed: boolean;
}

const props = defineProps<{
  tasks: TaskType[];
}>();

const emit = defineEmits<{
  (e: "update-task", updatedTask: TaskType): void;
  (e: "delete-task", taskId: string): void;
}>();

const handleUpdateTask = (updatedTask: TaskType) => {
  emit("update-task", updatedTask);
};

const handleDeleteTask = (taskId: string) => {
  emit("delete-task", taskId);
};
</script>

<template>
  <section>
    <div class="site-container">
      <TasksHeader :tasks="tasks" />
      <div class="flex flex-col gap-3 pt-6">
        <Task
          v-for="task in tasks"
          :key="task.id"
          :task="task"
          @update-task="handleUpdateTask"
          @delete-task="handleDeleteTask"
        />
      </div>
    </div>
  </section>
</template>
