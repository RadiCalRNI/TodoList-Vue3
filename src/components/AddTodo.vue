<template>
  <div class="card add">
    <div class="cb-container">
      <button id="add-btn" @click="addTodo">+</button>
    </div>
    <div class="txt-container">
      <label for="addt">افزودن </label>
      <input
        type="text"
        class="txt-input"
        placeholder="افزودن وظیفه جدید..."
        spellcheck="false"
        autocomplete="off"
        id="addt"
        dir="rtl"
        v-model="todoText"
        @keypress.enter="addTodo"
      />
    </div>
  </div>
</template>

<script>
export default {
  data() {
    return {
      todoText: "",
    };
  },

  methods: {
    addTodo() {
      this.$emit("addTodo", this.todoText);
      this.todoText = "";
    },
  },
};
</script>

<style></style>
