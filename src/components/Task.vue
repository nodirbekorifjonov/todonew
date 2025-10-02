<script setup lang="ts">
import { defineProps, ref } from "vue";

defineProps({
  task: {
    type: Object,
  },
});

const completed = ref<boolean>(true);
</script>

<template>
  <div
    class="p-4 rounded-lg flex gap-4 bg-[#262626] border"
    :class="completed ? 'border-[#262626]' : 'border-[#333333]'"
  >
    <div class="checkbox-wrapper-18">
      <div class="round">
        <label>
          <input type="checkbox" :checked="completed" />
          <span class="custom-check"></span>
        </label>
      </div>
    </div>
    <p
      class="text-sm font-inter"
      :class="completed ? 'text-[#808080] line-through' : 'text-[#F2F2F2]'"
    >
      {{ task?.text }}
    </p>
    <div class="flex gap-1 ml-auto">
      <button
        class="text-[#808080] text-sm py-[5px] px-1.5 rounded-sm bg-transparent w-6 h-6 flex justify-center items-center cursor-pointer hover:text-yellow-500 hover:bg-[#333333]"
      >
        <i class="fa-solid fa-pencil"></i>
      </button>
      <button
        class="text-[#808080] text-sm py-[5px] px-1.5 rounded-sm bg-transparent w-6 h-6 flex justify-center items-center cursor-pointer hover:text-[#E25858] hover:bg-[#333333]"
      >
        <i class="fa-solid fa-trash-can"></i>
      </button>
    </div>
  </div>
</template>

<style scoped>
.round label {
  display: inline-flex;
  align-items: center;
  cursor: pointer;
}

.round input[type="checkbox"] {
  display: none;
}

.custom-check {
  width: 20px;
  height: 20px;
  border: 2px solid #4ea8de;
  border-radius: 50%;
  display: inline-block;
  position: relative;
}

.custom-check::after {
  content: "";
  position: absolute;
  top: 2px;
  left: 5px;
  width: 6px;
  height: 10px;
  border: solid white;
  border-width: 0 2px 2px 0;
  transform: rotate(45deg);
  opacity: 0;
}

.round input[type="checkbox"]:checked + .custom-check {
  background-color: #5e60ce;
  border-color: #5e60ce;
}

.round input[type="checkbox"]:checked + .custom-check::after {
  opacity: 1;
}
</style>
