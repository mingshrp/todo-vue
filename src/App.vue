<script>
import ToDoItem from "./components/ToDoItem.vue";
import { nanoid } from "nanoid";

export default {
  name: "app",
  components: {
    ToDoItem,
  },
  data() {
    return {
      ToDoItems: [
        { id: `todo-${nanoid()}`, label: "Learn Vue", done: false },
        {
          id: `todo-${nanoid()}`,
          label: "Create a Vue project with the CLI",
          done: true,
        },
        { id: `todo-${nanoid()}`, label: "Have fun", done: true },
        {
          id: `todo-${nanoid()}`,
          label: "Create a to-do list",
          done: false,
        },
      ],
    };
  },
};

</script>

<template>
  <div id="app">
  <h1>To-Do List</h1>
 <ul>
  <li v-for="item in ToDoItems" :key="item.id">
    <to-do-item :label="item.label" :done="item.done"></to-do-item>
  </li>
</ul>
</div>
</template>


<style scoped></style>
