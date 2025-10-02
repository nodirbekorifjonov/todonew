<script setup lang="ts">
import Button from "./Button.vue";
import Input from "./Input.vue";

import { v4 as uuidv4 } from "uuid";

const task = {
  id: uuidv4(),
  text: "",
  completed: false,
};

const handleTaskText = (value: string) => {
  task.text = value;
};

const handleSubmitTask = () => {};
</script>

<template>
  <section class="w-full">
    <div class="site-container">
      <form @submit.prevent="handleSubmitTask" class="flex gap-2">
        <Input @taskText="handleTaskText" />
        <Button class="shrink-0" />
      </form>
    </div>
  </section>
</template>

<style scoped></style>
