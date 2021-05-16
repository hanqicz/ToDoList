<template>
  <div class="todo-item" v-bind:class="{ isComplete: todo.completed }">
    <p>
      <input type="checkbox" v-on:change="markComplete" />
      <span v-if="!isEditing">{{ todo.title }} {{ todo.date }}</span>
      <input v-else type="text" v-model="todo.title" />
      <button v-on:click="isEditing = !isEditing">Editar</button>
      <v-btn color="primary" elevation="4" icon></v-btn>
      <v-btn icon color="primary" v-on:click="$emit('del-todo', todo.id)">
        <v-icon color="primary">mdi-trash-can-outline</v-icon>
      </v-btn>
      <v-btn class="mx-2" fab dark small color="pink">
        <v-icon dark> mdi-heart </v-icon>
      </v-btn>
    </p>
  </div>
</template>

<script>
export default {
  name: "TodoItem",
  data() {
    return {
      isEditing: false,
    };
  },
  props: ["todo"],
  methods: {
    markComplete() {
      this.todo.completed = !this.todo.completed;
    },
  },
};
</script>

<style scoped>
.todo-item {
  background: #f4f4f4;
  padding: 10px;
  border-bottom: 1px #ccc dotted;
}

.isComplete {
  text-decoration: line-through;
}

.del {
  background: #ff0000;
  color: #fff;
  border: none;
  padding: 5px 9px;
  border-radius: 50%;
  cursor: pointer;
  float: right;
}
</style>
