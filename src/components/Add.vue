<template>
  <div v-if="!isEditing">
    <input
      type="text"
      v-model="title"
      name="title"
      placeholder="agregar tarea"
    />
    <input v-model="date" type="datetime-local" name="date" />
    <input type="submit" value="Agregar" v-on:click="agregarTarea" />
  </div>

  <div v-else>
    <input
      type="text"
      v-model="title"
      name="title"
      placeholder="editar tarea"
    />
    <input v-model="date" type="datetime-local" name="date" />
    <input type="submit" value="Editar" v-on:click="editar" />
  </div>
</template>

<script>
import { nanoid } from "nanoid";

export default {
  name: "Add",
  data() {
    return {
      title: "",
      date: "",
      isEditing: false,
    };
  },
  methods: {
    agregarTarea() {
      const nuevaTarea = {
        id: nanoid(),
        title: this.title,
        date: this.date,
        completed: false,
      };
      this.$emit("agregar", nuevaTarea);
    },
    editar() {
      this.isEditing = !this.isEditing;
    },
    created() {
      this.$parent.$on("editing", this.editar);
    },
  },
};
</script>

<style scoped>
</style>