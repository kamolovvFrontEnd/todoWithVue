<script setup>
import { ref } from "vue";

const text = ref("");
const id = 0
const todos = ref([]);

const onSubmitHandler = (e) => {
  e.preventDefault();
  text.value = ""
  id.value++
  console.log(id.value);
};
</script>

<template>
  <div>
    <h1>Todo App</h1>
    <form @submit="onSubmitHandler">
      <input v-model="text" type="text" placeholder="Enter ..." />
      <button type="submit" @click="todos.push({text, id})">Submit</button>
      <button @click="todos.sort((a, b) => a.id > b.id ? 1 : -1)">sort by id</button>
    </form>
  </div>

  <div>
    <ol>
      <li v-for="(todo, i) in todos">
        {{ todo.text }}
        <button @click="todos.splice(i, 1)">delete</button>
      </li>
    </ol>
  </div>
</template>

