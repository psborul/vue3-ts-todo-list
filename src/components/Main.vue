<template>
  <div class="container">
    <h1>TODO LIST</h1>
    <TodoList />
  </div>
</template>

<script lang="ts">
import { defineComponent } from "vue";
import TodoList from "./TodoList.vue";

export default defineComponent({
  components: {
    TodoList
  },
  name: "Main"
});
</script>

<style scoped>
.container {
  width: 1024px;
  margin: 0 auto;
}
</style>
