<template>
  <div class="h-40 overflow-auto">
    <div v-for="todo in todoList" :key="todo.id">
      <div
        class="flex justify-between items-center p-2 border border-r-cyan-400"
      >
        <span :class="{ completed: todo.completed }">{{ todo.item }}</span>
        <div>
          <span @click.stop="toggleCompleted(todo.id)" class="cursor-pointer"
            >&#10004;</span
          >
          <span @click="deleteTodo(todo.id)" class="cursor-pointer"
            >&#10060;</span
          >
        </div>
      </div>
    </div>
  </div>
</template>

<script lang="ts">
import { defineComponent } from "vue";
import { useTodoListStore } from "../store/useTodoListStore";
import { storeToRefs } from "pinia";
export default defineComponent({
  setup() {
    const store = useTodoListStore();
    const { todoList } = storeToRefs(store);
    const { toggleCompleted, deleteTodo } = store;
    return { todoList, toggleCompleted, deleteTodo };
  },
});
</script>

<style>
.completed {
  text-decoration: line-through;
}
</style>