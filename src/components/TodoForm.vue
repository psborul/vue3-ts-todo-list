<template>
  <form
    @submit.enter.prevent="addItem"
    class="form"
  >
    <input
      v-model.trim="model.title"
      placeholder="Type..."
      class="form__input-title"
    />
    <select
      v-model="model.prior"
      class="form__select"
    >
      <option
        v-for="option in options"
        :value="option"
        :key="option"
      >{{ option }}</option>
    </select>
    <button
      type="submit"
      class="form__submit-btn"
    >SUBMIT</button>
  </form>
</template>

<script lang="ts">
import { defineComponent, ref, markRaw } from "vue";

class Model {
  title: string;
  prior?: number;
  id: Date;

  constructor(title = "", prior = 1, id = new Date()) {
    this.title = title;
    this.prior = prior;
    this.id = id;
  }
}

export default defineComponent({
  setup(props, { emit }) {
    const model = ref(new Model());

    const addItem = () => {
      emit("submit", model.value);
      model.value = new Model();
    };

    const options = markRaw<Number[]>([1, 2, 3]);

    return { model, addItem, options };
  },
  emits: ["submit"]
});
</script>

<style lang="scss" scoped>
.form {
  display: flex;
  justify-content: space-between;
  align-items: center;

  &__input-title {
    width: 70%;
    height: 50px;
    font-size: 24px;
  }

  &__select {
    margin-left: 50px;
    height: 50px;
    width: 50px;
  }

  &__submit-btn {
    width: 100px;
    height: 50px;
    margin-left: 50px;
  }
}
</style>