<template>
  <li>
    <h3>{{ item.title }}</h3>
    <p>{{ item.desc }}</p>
  </li>
</template>

<script>
export default {
  props: ["item"],
};
</script>

<style>
li {
  margin: 1rem 0;
  border: 1px solid #ccc;
  padding: 1rem;
  border-radius: 15px;
}

h3 {
  margin: 0.5rem 0;
}
</style>