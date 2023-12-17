<script setup>
import { ref } from "vue";

const text = ref("");
const id = 0;
const todos = ref([]);

const onSubmitHandler = (e) => {
  e.preventDefault();
  text.value = "";
  id.value++;
};
</script>

<template>
  <div>
    <span class="text-4xl ml-24">Todo App</span>
    <div>
      <form @submit="onSubmitHandler">
        <input
          v-model="text"
          type="text"
          placeholder="Enter ..."
          class="text-black p-2 m-5 rounded"
        />
        <button
          type="submit"
          class="bg-white text-black border rounded m-4 p-2 animation-for-button"
          @click="todos.push({ text, id })"
        >
          Submit
        </button>
        <button
          class="bg-white text-black border rounded m-1 p-2 animation-for-submit-button"
          @click="todos.sort((a, b) => (a.id > b.id ? 1 : -1))"
        >
          sort by id
        </button>
      </form>
    </div>

    <div>
      <ol>
        <li
          v-for="(todo, i) in todos"
          class="p-3 border border-solid border-r-2 rounded flex items-center justify-between bg-white text-black border-white m-5"
        >
          {{ todo.text }}
          <button
            class="border border-black text-right rounded p-2 content-end animation-for-delete-button"
            @click="todos.splice(i, 1)"
          >
            delete
          </button>
        </li>
      </ol>
    </div>
  </div>
</template>

<style>
.animation-for-button:hover {
  cursor: pointer;
  background-color: green;
  color: white;
  transition: transform 0.3s;
  transform: scale(1.3);
}
.animation-for-delete-button:hover {
  cursor: pointer;
  background-color: red;
  color: white;
  transition: transform 0.3s;
  transform: scale(1.3);
}
.animation-for-submit-button:hover {
  cursor: pointer;
  background-color: grey;
  color: white;
  transition: transform 0.3s;
  transform: scale(1.3);
}
</style>
