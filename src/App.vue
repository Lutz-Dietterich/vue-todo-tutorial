<template>
  <div class="bg-green-400 h-screen m-0 p-10">
    <div class="bg-gray-600/60 text-white w-1/2 m-auto mt-12 rounded-lg hover:shadow-lg shadow shadow-gray-800">
        <div class=" text-center py-5 mb-5 border-b-2 border-blacks">
          <h1 class="text-3xl py-4 flex justify-center gap-3"> <img class="flex justify-end" src="./assets/checklist.png" alt="">Unsere Todo's</h1>
          <p class="text-xl">Offene Todo's: {{ todos.length }}</p>
          <div class="flex justify-center bg-white w-4/5 mx-auto mt-5 rounded-full">
            <input type="text" class=" w-4/5 rounded-l-full text-gray-800 py-0.5 px-3" v-model="newTodo"/>
            <button class="bg-slate-500 w-1/5 rounded-r-full flex justify-center" @click="addTodo"><img class="self-center" src="./assets/add.png" alt=""></button>
          </div>
        </div>
        <div v-for="(todo, index) in todos" :key="todo.todo">
          <TodoList 
            :todoprop="todo" 
            :todoindex="index" 
            @toggledone-index="toggleDone"
            @removetodo-index="deleteTodo"
          />
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
      newTodo: "",
      todos: [
        {todo: "Einkaufen", done: false},
        {todo: "Sport", done: false},
        {todo: "Programmieren", done: true},
        {todo: "Lesen", done: false},

      ],
    };
  },
  methods: {
    toggleDone(index) {
      this.todos[index].done = !this.todos[index].done;
    },
    deleteTodo(index) {
      this.todos.splice(index, 1);
    },
    addTodo() {
      this.todos.push({todo: this.newTodo, done: false});
    },
  },
  components: {
    TodoList,
  },
};
</script>

