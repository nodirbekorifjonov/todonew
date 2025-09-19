<script setup lang="ts">
import Task from "./Task.vue";
import TasksHeader from "./TasksHeader.vue";
</script>

<template>
  <section>
    <div class="site-container">
      <TasksHeader />
      <div class="flex flex-col gap-3 pt-6">
        <Task />
        <Task />
      </div>
    </div>
  </section>
</template>

<style scoped></style>
