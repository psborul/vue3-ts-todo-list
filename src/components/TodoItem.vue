<template>
  <div class="item">
    <p class="item__title">{{ item.title }}</p>
    <p class="item__prior">Priority: {{ item.prior }}</p>
    <button
      class="item__delete-btn"
      @click="$emit('delete')"
    >DELETE</button>
  </div>
</template>

<script lang="ts">
import { defineComponent } from "vue";

export default defineComponent({
  props: {
    item: {
      type: Object,
      default: () => ({})
    }
  }
});
</script>

<style lang="scss" scoped>
.item {
  display: flex;
  align-items: center;
  font-size: 24px;
  font-weight: 500;

  &__title {
    text-transform: uppercase;
    width: 500px;
    text-align: start;
    overflow: scroll;
  }

  &__prior {
    margin-left: auto;
  }

  &__delete-btn {
    width: 100px;
    height: 50px;
    margin-left: auto;
  }
}
</style>