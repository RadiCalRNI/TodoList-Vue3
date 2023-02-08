<template>
  <div class="card stat">
    <p class="corner">
      <span id="items-left">{{ counter }}</span> مورد باقی مانده
    </p>
    <div class="filter">
      <button id="all" class="on">همه</button>
      <button id="active">فعال</button>
      <button id="completed">تکمیل</button>
    </div>
    <div class="corner">
      <button id="clear-completed" @click="deleteCompleted">
        حذف تکمیل شده ها
      </button>
    </div>
  </div>
</template>

<script>
export default {
  props: {
    counter: Number,
  },
  methods: {
    deleteCompleted() {
      if (confirm("آیا از حذف تسک های انجام شده اطمینان دارید؟")) {
        this.$emit("deleteCompleted");
      }
    },

    unCheckedTask() {
      this.$emit("unCheckedTask");
    },
  },
  computed: {},
};
</script>

<style></style>
