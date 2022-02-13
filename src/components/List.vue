<script setup>
import useTodos from "../composables/useTodos";
const {pending, completed, changeStatus} = useTodos();

defineProps({
    isCompleted: {
        default: false,
        type: Boolean,
    },
});
</script>


<template>

<div class="w-1/3 space-y-4">
    <h3 class="text-2xl font-bold text-center" :class="isCompleted ? 'text-red-400' : 'text-purple-400' " >{{ isCompleted ? "Completed" : "Pending" }}</h3>
    <ul class="pt-8 space-y-4">
      <li v-for="todo in isCompleted ? completed : pending"
      :key="todo.id"
      @click="changeStatus(todo.id)"
      :class="isCompleted ? 'text-red-600 hover:bg-red-400' : 'text-purple-600 hover:bg-purple-400'"
      class="w-full px-4 py-2 font-bold text-center duration-500 bg-red border-2 border-black rounded-lg hover:cursor-pointer hover:bg-yellow-400 hover:text-black trasition-colors">
      {{todo.content}}
      </li>
      
    </ul>
    </div>
</template>