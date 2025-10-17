<script setup lang="ts">
const props = defineProps<{
  tasks: { id: string; text: string; completed: boolean }[];
}>();
</script>

<template>
  <div class="flex justify-between items-center">
    <div class="flex items-center gap-2 font-interBold">
      <h5 class="text-[#4EA8DE] text-sm">Tasks created</h5>
      <span
        class="py-0.5 px-2 bg-[#262626] rounded-full text-xs text-[#D9D9D9]"
      >
        {{ props.tasks.length }}
      </span>
    </div>
    <div class="flex items-center gap-2 font-interBold">
      <h5 class="text-[#8284FA] text-sm">Completed</h5>
      <span
        class="py-0.5 px-2 bg-[#262626] rounded-full text-xs text-[#D9D9D9]"
      >
        {{ props.tasks.filter((task) => task.completed).length }}
      </span>
    </div>
  </div>
</template>

<style scoped></style>
