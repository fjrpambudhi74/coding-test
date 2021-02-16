<template>
  <div>
    <h3>User Overview</h3>
    <p>User id is {{ $route.params.id }}</p>
    <p>Status : {{ $route.query.status }}</p>
    <button @click="goHome">Go Home</button>
  </div>
</template>

<script>
export default {
  data() {
    return {};
  },
  methods: {
    goHome() {
      this.$router.push("/");
    },
  },
  beforeRouteEnter(to, from, next) {
    console.log("Welcome to the swamp!");
    next();
  },
  beforeRouteLeave(to, from, next) {
    const answer = window.confirm("Are you sure you want to leave?");

    if (answer) {
      next();
    } else {
      next(false);
    }
  },
};
</script>

<style>
</style>