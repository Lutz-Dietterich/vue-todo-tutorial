<template>
  <div>
    <h1>{{ message.toUpperCase() }}</h1>
    <h1>{{ count }}</h1>
    <button @click="countUp">Hochzählen</button>
  </div>
</template>

<script>
export default {
  name: 'TodoList',
  data() {
    return {
      message: "HellO World",
      count: 0,
    };
  },
  methods: {
    countUp() {
      this.count++;
    },
  },
};
</script>

