<template>
  <div class="px-2 py-1 flex justify-between items-center" @click="toggleTodo">
    <h1 class="p-1 cursor-pointer" :class="{'line-through font-thin': this.todo.done}">{{ todo.todo }}</h1>
    <button class="hover:scale-110" @click="removeTodo"><img src="../assets/delete.png" alt="delete Todo"></button>
  </div>
</template>

<script>
export default {
  name: 'TodoList',
  props: ["todoprop", "todoindex"],
  data() {
    return {
      todo: this.todoprop,
    };
  },
  methods: {
    toggleTodo() {
      this.$emit("toggledone-index", this.todoindex)
    },
    removeTodo() {
      this.$emit("removetodo-index", this.todoindex)
    },
  },
};
</script>

