
<template>
  <form @submit.prevent="addItemAndClear(todo)">
    <input
      v-model="todo"
      type="text"
      class="
        border border-indigo-600
        outline outline-2 outline-offset-2
        py-2
        px-3
      "
    /><button class="outline outline-2 outline-offset-2 ml-4 py-2 px-3">
      Add
    </button>
  </form>
</template>

<script lang="ts">
import { ref, defineComponent } from "vue";
import { useTodoListStore } from "../store/useTodoListStore";
export default defineComponent({
  setup() {
    const todo = ref("");
    const store = useTodoListStore();
    function addItemAndClear(item: string) {
      if (item.length === 0) {
        return;
      }
      store.addTodo(item);
      todo.value = "";
    }
    return { todo, addItemAndClear };
  },
});
</script>

<style lang="scss" scoped></style>