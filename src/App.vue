<template>
  <div class="bg-green-400 h-screen m-0 p-10">
    <article class="bg-gray-600/60 text-white w-1/2 m-auto mt-12 rounded-lg hover:shadow-lg shadow shadow-gray-800">
        <section class=" text-center py-5 mb-5 border-b-2 border-blacks">
          <h1 class="text-3xl py-4 flex justify-center gap-3">
            <img class="flex justify-end" src="./assets/checklist.png" alt="">Todo's
          </h1>
          <p class="text-xl" v-if="openTodos.length > 0">
            Offene Todo's: {{ openTodos.length }}
          </p>
          <p class="text-xl" v-else>
            Alles erledigt! 
          </p>
          <div class="flex justify-center bg-white w-4/5 mx-auto mt-5 rounded-full">
            <input type="text" required @keyup.enter="addTodo" class=" w-4/5 rounded-l-full text-gray-800 py-0.5 px-3" v-model="newTodo"/>
            <button class="bg-slate-500 w-1/5 rounded-r-full flex justify-center" @click="addTodo"><img class="self-center" src="./assets/add.png" alt=""></button>
          </div>
        </section>
        <div v-for="(todo, index) in todos" :key="todo.todo">
          <TodoList 
            :todoprop="todo" 
            :todoindex="index" 
            @toggledone-index="toggleDone"
            @removetodo-index="deleteTodo"
          />
        </div>
    </article>
  </div>
</template>

<script>
import TodoList from './components/TodoList.vue'

export default {
  name: 'App',
  data() {
    return {
      newTodo: "",
      todos: [],
    };
  },
  methods: {
    toggleDone(index) {
      this.todos[index].done = !this.todos[index].done;
      this.storeTodos();
    },
    deleteTodo(index) {
      this.todos.splice(index, 1);
      this.storeTodos();
    },
    addTodo() {
      if (this.newTodo.length > 0) {
      this.todos.push({todo: this.newTodo, done: false});
      this.storeTodos();
      this.newTodo = '';
      } else {
        alert("Du muss schon was schreiben.");
      }
    },
    storeTodos() {
      localStorage.setItem("todos", JSON.stringify(this.todos));
    }
  },
  mounted() {
    let data = localStorage.getItem("todos");
    if (data !== "" && data !== null) {
    this.todos = JSON.parse(data);
    } else {
      this.todos = [];
    }
  },
  computed: {
    openTodos() {
      const openTodos = this.todos.filter((todo) => {
        return !todo.done;
      });
      return openTodos;
    },
  },
  components: {
    TodoList,
  },
};
</script>

