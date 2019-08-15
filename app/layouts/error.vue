<template>
  <div class="section">
    <h1 v-if="error.statusCode === 404">Page not found</h1>
    <h1 v-else>An error occurred</h1>
    <nuxt-link to="/">Home page</nuxt-link>
  </div>
</template>

<script>
export default {
  props: ["error"]
};
</script>

<style scoped>
.section {
  text-align: center;
}
h1 {
  font-size: 30pt;
}
</style>
