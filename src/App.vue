<script>
import ToDoItem from "./components/ToDoItem.vue";

export default {
  name: "App",
  components: {
    ToDoItem,
  },
};
</script>

<template>
  <div id="app">
  <h1>To-Do List</h1>
  <ul>
    <li>
      <to-do-item label="My ToDo Item" :done="true"></to-do-item>
    </li>
  </ul>
</div>
</template>


<style scoped></style>
