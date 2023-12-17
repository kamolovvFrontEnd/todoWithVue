<script setup>
import { ref } from "vue";

let text = ref("");
const todos = ref([]);

const onSubmitHandler = (e) => {
  text.value = ""
  e.preventDefault();
};
</script>

<template>
  <div>
    <h1>Todo App</h1>
    <form @submit="onSubmitHandler">
      <input v-model="text" type="text" placeholder="Enter ..." />
      <button type="submit" @click="todos.push(text)">Submit</button>
    </form>
  </div>

  <div>
    <ol>
      <li v-for="(todo, i) in todos">
        {{ todo }}
        <button @click="todos.splice(i, 1)">delete</button>
      </li>
    </ol>
  </div>
</template>

