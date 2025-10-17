<script setup lang="ts">
import Button from "./Button.vue";
import { v4 as uuidv4 } from "uuid";
import { reactive } from "vue";

const task = reactive({
  id: uuidv4(),
  text: "",
  completed: false,
});

const handleSubmitTask = () => {
  const newTask = { ...task };
  emit("add-task", newTask);
  // Reset task
  task.id = uuidv4();
  task.text = "";
  task.completed = false;
};

const emit = defineEmits(["add-task"]);
</script>

<template>
  <section class="w-full">
    <div class="site-container">
      <form @submit.prevent="handleSubmitTask" class="flex gap-2">
        <input
          type="text"
          v-model="task.text"
          placeholder="Add a new task"
          class="bg-[#262626] rounded-lg p-4 w-full border border-[#0D0D0D] text-[#F2F2F2] text-[16px] font-inter leading-[1.4] outline-none focus:border-[#5E60CE] placeholder:text-[#808080]"
        />
        <Button class="shrink-0" />
      </form>
    </div>
  </section>
</template>

<style scoped></style>
