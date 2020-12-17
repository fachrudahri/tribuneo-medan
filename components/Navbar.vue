<template>
  <nav class="navbar mb-6" role="navigation" aria-label="main navigation">
  <div class="navbar-brand">
    <a class="navbar-item" href="https://bulma.io">
      <img src="https://bulma.io/images/bulma-logo.png" width="112" height="28">
    </a>

    <a role="button" class="navbar-burger burger" aria-label="menu" aria-expanded="false" data-target="navbarBasicExample">
      <span aria-hidden="true"></span>
      <span aria-hidden="true"></span>
      <span aria-hidden="true"></span>
    </a>
  </div>

  <div id="navbarBasicExample" class="navbar-menu">
    <div class="navbar-end">
      <div class="navbar-item">
        <nuxt-link to="/" class="navbar-item">Home</nuxt-link>
        <nuxt-link to="/blog" class="navbar-item">Blog</nuxt-link>
        </div>
      </div>
    </div>
</nav>
</template>

<script>
export default {
  name: 'Navbar',
  head: {
    script: [
      {
        src: '/bulma.js'
      }
    ]
  }
};
</script>

<style>
</style>
