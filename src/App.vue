<script setup>
import Title from "./components/Title.vue";
import List from "./components/List.vue";
import useTodos from "./composables/useTodos";
const {pending, completed, changeStatus} = useTodos();
</script>

<template>
<div class="min-h-screen bg-yellow-400">
  <div class="container flex flex-col pt-8 mx-auto space-y-8">
    <Title />
  <div class="flex justify-around">
    <List />
    <List isCompleted />
  </div>
  </div>
  </div>
</template>
