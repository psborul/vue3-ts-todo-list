<template>
  <ul class="list">
    <TodoForm @submit="addItem" />
    <li
      v-for="item in items"
      :key="item.id"
    >
      <TodoItem
        :item="item"
        @delete="deleteItem(item.id)"
      />
    </li>
  </ul>

</template>

<script lang="ts">
import TodoForm from "./TodoForm.vue";
import TodoItem from "./TodoItem.vue";

import { defineComponent, ref } from "vue";

type TodoItem = {
  title: string;
  prior?: number;
  id: number;
}

export default defineComponent({
  name: "TodoList",
  components: {
    TodoForm,
    TodoItem
  },
  setup() {
    const items = ref<TodoItem[]>([]);

    const addItem = (item: TodoItem) => {
      items.value = [...items.value, item];
    };

    const deleteItem = (id: number) => {
      items.value = items.value.filter(item => item.id !== id);
    };

    return { items, addItem, deleteItem };
  }
});
</script>

<style scoped lang="scss">
.list {
  list-style: none;
}
</style>