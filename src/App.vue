<script setup>
import {ref, computed} from "vue";

const newTodo = ref("");
const todos = ref([]);

  const pending = computed(() => {
    return todos.value.filter((todo) => !todo.done);
  });

  const completed = computed(() => {
    return todos.value.filter((todo) => todo.done);
  });


  const addTodo = () => {
    if(newTodo.value.trim()) {
    todos.value.push({
      id: todos.value.length,
      content: newTodo.value,
      done: false,
      });
      newTodo.value = "";
    }
  };

  const changeStatus = (id) => {
      const todo = todos.value.find((todo) => todo.id == id);
      todo.done = !todo.done;
    
  };
</script>

<template>
<div class="min-h-screen bg-yellow-400">
  <div class="container flex flex-col pt-8 mx-auto space-y-8">
  <h1 class="pb-4 text-6xl font-black tracking-tighter text-center text-black-300 ">My Todo App</h1>
  <input
  @change ="addTodo"
  v-model="newTodo" 
  type="text" class="rounded-lg text-center px=4 py-2 text-xl text-white bg-black" placeholder="Add a new todo function."/>
  <div class="flex justify-around">
  <div class="w-1/3 space-y-4">
    <h3 class="text-2xl font-bold text-center text-black ">Pending</h3>
    <ul class="pt-8 space-y-4">
      <li v-for="todo in pending"
      :key="todo.id"
      @click="changeStatus(todo.id)"
      class="w-full px-4 py-2 font-bold text-center text-yellow-400 duration-500 bg-black border-2 border-black rounded-lg hover:cursor-pointer hover:bg-yellow-400 hover:text-black trasition-colors">
      {{todo.content}}
      </li>
      
    </ul>
    </div>
    <div class="w-1/3 space-y-4">
        <h3 class="text-2xl font-bold text-center text-green-600 ">Completed</h3>

    <ul class="pt-8 space-y-4">
      <li 
      v-for="todo in completed"
      :key="todo.id"
      @click="changeStatus(todo.id)"
      class="w-full px-4 py-2 font-bold text-center text-white duration-500 bg-green-600 rounded-lg hover:cursor-pointer border-green hover:bg-white hover:text-green-600 trasition-colors"> {{todo.content}}</li>
    </ul>
  </div>
  </div>
  </div>
  </div>
</template>
