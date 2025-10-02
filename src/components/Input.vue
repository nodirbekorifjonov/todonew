<script setup lang="ts">
import { ref, watch } from "vue";

const text = ref<string>("");

const emit = defineEmits<{
  (e: "taskText", value: string): void;
}>();

watch(text, (newVal) => {
  emit("taskText", newVal);
});
</script>

<template>
  <input
    type="text"
    v-model="text"
    placeholder="Add a new task"
    class="bg-[#262626] rounded-lg p-4 w-full border border-[#0D0D0D] text-[#F2F2F2] text-[16px] font-inter leading-[1.4] outline-none focus:border-[#5E60CE] placeholder:text-[#808080]"
  />
</template>

<style scoped></style>
