<template>
  <div>
    <nav class="navbar header has-shadow" role="navigation" aria-label="main navigation">
      <div class="navbar-brand">
        <a class="navbar-item" href="/">
          <img src="~assets/logo-color.svg" alt="Trivago Magazine Logo" height="28" />
        </a>
      </div>
      <div class="navbar-menu">
        <div class="navbar-end">
          <nuxt-link to="/" class="navbar-item">Home</nuxt-link>
        </div>
      </div>
    </nav>

    <div>
      <nuxt />
    </div>

    <Footer />
  </div>
</template>

<script>
import Footer from "../components/Footer";

export default {
  components: {
    Footer
  },
  data() {
    return {
      items: [
        {
          title: "Home",
          icon: "home",
          to: { name: "index" }
        }
      ]
    };
  }
};
</script>

<style>
@import url("https://fonts.googleapis.com/css?family=Ubuntu&display=swap");

body {
  font-family: "Ubuntu", sans-serif;
}
</style>
