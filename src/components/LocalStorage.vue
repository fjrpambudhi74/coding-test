<template>
  <div>
    <h2 class="my-5">Local Storage Example</h2>
    <p>You have seen this websites {{ countstore }} times.</p>
    <p class="text-muted">Enjoy the websites &#128565;</p>
  </div>
</template>

<script>
export default {
  data() {
    return {};
  },
  mounted() {
    if (!localStorage.getItem("countstore"))
      localStorage.setItem("countstore", 0);
    localStorage.setItem("countstore", +localStorage.getItem("countstore") + 1);
  },
  computed: {
    countstore() {
      return localStorage.getItem("countstore");
    },
  },
};
</script>

<style>
</style>