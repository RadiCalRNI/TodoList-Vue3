<template>
  <app-header></app-header>
  <main>
    <add-todo></add-todo>
    <ul class="todos">
      <todo-item></todo-item>
    </ul>
    <app-stat></app-stat>
  </main>
  <app-footer></app-footer>
</template>

<script>
import AppHeader from "./components/AppHeader.vue";
import AddTodo from "./components/AddTodo.vue";
import TodoItem from "./components/TodoItem.vue";
import AppFooter from "./components/AppFooter.vue";
import AppStat from "./components/AppStat.vue";
export default {
  components: {
    AppHeader,
    AddTodo,
    TodoItem,
    AppFooter,
    AppStat,
  },
};
</script>

<style></style>
