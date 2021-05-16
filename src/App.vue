<template>
  <div id="app">
    <Header />
    <Add v-on:agregar="agregarTarea" />
    <Todos v-bind:todos="todos" v-on:del-todo="deleteTodo" />
  </div>
</template>

<script>
import Todos from "./components/Todos";
import Add from "./components/Add.vue";
import Header from "./components/Header";

export default {
  name: "App",
  components: {
    Todos,
    Add,
    Header,
  },

  data() {
    return {
      todos: [],
    };
  },

  methods: {
    deleteTodo(id) {
      this.todos = this.todos.filter((todo) => todo.id !== id);
    },
    agregarTarea(nuevaTarea) {
      this.todos.push(nuevaTarea);
    },
  },
};
</script>

<style>
body {
  font-family: Arial, Helvetica, sans-serif;
  line-height: 1.4;
}
</style>
