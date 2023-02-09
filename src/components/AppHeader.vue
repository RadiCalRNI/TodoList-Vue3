<template>
  <header class="card">
    <h1>لیست وظایف</h1>
    <button id="theme-switcher" @click="changeTheme">
      <img
        v-if="defaultTheme == 'dark'"
        src="../assets/images/icon-sun.svg"
        alt="Change color theme"
      />
      <img
        v-else
        src="../assets/images/icon-moon.svg"
        alt="Change color theme"
      />
    </button>
  </header>
</template>

<script>
export default {
  data() {
    return {
      defaultTheme: "dark",
    };
  },
  methods: {
    changeTheme() {
      if (this.defaultTheme == "dark") {
        this.defaultTheme = "light";
        document.body.classList.add("light");
      } else {
        this.defaultTheme = "dark";
        document.body.classList.remove("light");
      }
    },
  },
};
</script>

<style></style>
