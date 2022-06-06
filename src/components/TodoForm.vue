<template>
  <form @submit.prevent="eventform($event)">
    <input type="radio" name="checkBox" class="check-task" disabled />
    <input
      type="text"
      class="input-task"
      placeholder="Create a new todo..."
      v-model.trim="text"
    />
  </form>
</template>

<script>
import { inject, ref } from "vue";
export default {
  setup() {
    const todos = inject("todos");
    const text = ref("");

    const eventform = (e) => {
      e.preventDefault();
      if (text.value != "") {
        const todo = {
          text: text.value,
          state: false,
          id: Date.now(),
        };
        text.value = "";
        todos.value.push(todo);
        console.log(1);
      } else {
        alert("Enter Task");
      }
    };

    return { eventform, text };
  },
};
</script>

<style>
</style>