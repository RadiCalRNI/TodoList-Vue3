<template>
  <app-header></app-header>
  <main>
    <add-todo @addTodo="addNewTodo"></add-todo>

    <ul class="todos">
      <todo-item
        v-for="task in todoList"
        :key="task.key"
        :todo="task"
        @delete="deleteTodo"
        @checked="checked"
      ></todo-item>
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

  data() {
    return {
      todoList: [],
    };
  },

  methods: {
    addNewTodo(title) {
      const key = Math.random().toString(16).slice(2);
      const isComplete = false;
      const task = { key, title, isComplete };
      this.todoList.push(task);
    },

    deleteTodo(key) {
      this.todoList = this.todoList.filter((item) => item.key != key);
    },

    checked(key, isComplete) {
      this.todoList.forEach((item) => {
        if (item.key == key) {
          item.isComplete = isComplete;
        }
      });
    },
  },
};
</script>

<style></style>
