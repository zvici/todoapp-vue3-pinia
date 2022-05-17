<template>
  <todo-app />
</template>

<script lang="ts">
import { defineComponent } from "vue";
import TodoApp from "./components/TodoApp.vue";
export default defineComponent({
  name: "App",
  components: {
    TodoApp,
  },
});
</script>

<style>
#app {
  width: 100%;
  height: 100vh;
  display: flex;
  justify-content: center;
  align-items: center;
}
</style>