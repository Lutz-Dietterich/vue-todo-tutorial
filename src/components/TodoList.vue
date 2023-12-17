<template>
  <div class="px-2 py-1 flex justify-between items-center" @click="logindex()">
    <h1 class="p-1 cursor-pointer" :class="{'line-through font-thin': this.todo.done}">{{ todo.todo }}</h1>
    <button class="hover:scale-110"><img src="../assets/delete.png" alt="delete Todo"></button>
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
    logindex() {
    console.log(this.todoindex)
    }
  },
};
</script>

