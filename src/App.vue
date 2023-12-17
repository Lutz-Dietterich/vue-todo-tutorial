<template>
  <div class="bg-green-400 h-screen m-0 p-10">
    <div class="bg-gray-600/60 text-white w-1/2 m-auto mt-12 rounded-lg hover:shadow-lg shadow shadow-gray-800">
        <div class=" text-center py-5 mb-5 border-b-2 border-blacks">
          <h1 class="text-3xl py-4 ">Unsere Todo's</h1>
          <p class="text-xl">Offene Todo's: {{ todos.length }}</p>
        </div>
        <div v-for="(todo, index) in todos" :key="todo.todo">
          <TodoList :todoprop="todo" :todoindex="index"/>
        </div>
    </div>
  </div>
</template>

<script>
import TodoList from './components/TodoList.vue'

export default {
  name: 'App',
  data() {
    return {
      todos: [
        {todo: "Einkaufen", done: false},
        {todo: "Sport", done: false},
        {todo: "Programmieren", done: true},
        {todo: "Lesen", done: false},

      ],
    };
  },
  components: {
    TodoList,
  },
};
</script>

