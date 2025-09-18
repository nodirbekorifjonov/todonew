<script setup lang="ts">
import Button from "./Button.vue";
import Input from "./Input.vue";
</script>

<template>
  <section class="w-full">
    <div class="site-container">
      <form class="flex gap-2">
        <Input />
        <Button class="shrink-0" />
      </form>
    </div>
  </section>
</template>

<style scoped></style>
