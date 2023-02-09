<template>
  <div class="card stat">
    <p class="corner">
      <span id="items-left">{{ counter }}</span> مورد باقی مانده
    </p>
    <div class="filter">
      <button id="all" :class="{ on: activeTab === 'all' }" @click="changeTab('all')">همه</button>
      <button id="active" :class="{ on: activeTab === 'active' }" @click="changeTab('active')">فعال</button>
      <button id="completed" :class="{ on: activeTab === 'completed' }" @click="changeTab('completed')">تکمیل</button>
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
  data() {
    return {
      activeTab: "all",
    };
  },
  props: {
    counter: Number,
  },
  methods: {
    deleteCompleted() {
      if (confirm("آیا از حذف تسک های انجام شده اطمینان دارید؟")) {
        this.$emit("deleteCompleted");
      }
    },

    changeTab(status) {
      this.activeTab = status;
      this.$emit("activeTab", this.activeTab);
    },
  },
};
</script>

<style></style>
