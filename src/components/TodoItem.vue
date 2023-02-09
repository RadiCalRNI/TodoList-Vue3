<template>
  <li class="card" draggable="true">
    <div class="cb-container">
      <input
        type="checkbox"
        class="cb-input"
        :checked="todo.isComplete ? true : false"
        @click="checked"
      />
      <span class="check"></span>
    </div>
    <p class="item">
      <del v-if="todo.isComplete">{{ todo.title }}</del>
      <span v-else v-text="todo.title"></span>
    </p>
    <button class="clear" @click="deleteTodo">
      <img src="../assets/images/icon-cross.svg" alt="Clear it" />
    </button>
  </li>
</template>

<script>
export default {
  props: {
    todo: Object,
  },

  methods: {
    deleteTodo() {
      if (confirm("آیا از حذف تسک مطعمن هستید؟")) {
        this.$emit("delete", this.todo.key);
      }
    },

    checked() {
      this.$emit("checked", this.todo.key, !this.todo.isComplete);
    },
  },
};
</script>

<style></style>
