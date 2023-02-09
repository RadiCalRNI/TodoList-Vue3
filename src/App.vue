<template>
  <app-header></app-header>
  <main>
    <add-todo @addTodo="addNewTodo"></add-todo>

    <ul class="todos">
      <todo-item
        v-for="(task, index) in list"
        :key="task.key"
        :todo="task"
        @delete="deleteTodo"
        @checked="checked"
        @dragover.prevent
        @dragstart="dragStart(index)"
        @drop="dragEnd(index)"
      ></todo-item>
    </ul>

    <app-stat
      @deleteCompleted="deleteCompleted"
      :counter="unCheckedTask"
      @activeTab="getTodo"
    ></app-stat>
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
      dragging: -1,
      tab: "",
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

    deleteCompleted() {
      this.todoList = this.todoList.filter((item) => item.isComplete === false);
    },

    dragStart(index) {
      this.dragging = index;
    },

    dragEnd(index) {
      const element = this.todoList.splice(this.dragging, 1)[0];
      this.todoList.splice(index, 0, element);
    },

    getTodo(activeTab) {
      this.tab = activeTab;
    },
  },

  computed: {
    unCheckedTask() {
      let unCheckedTasks = this.todoList.filter(
        (item) => item.isComplete == false
      );
      return unCheckedTasks.length;
    },
    list() {
      if (this.tab == "all") {
        return this.todoList;
      } else if (this.tab == "active") {
        return this.todoList.filter((item) => item.isComplete === false);
      } else if (this.tab == "completed") {
        return this.todoList.filter((item) => item.isComplete === true);
      } else {
        return this.todoList;
      }
    },
  },
};
</script>

<style></style>
