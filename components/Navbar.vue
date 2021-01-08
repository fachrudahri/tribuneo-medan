<template>
  <nav class="navbar py-4" role="navigation" aria-label="main navigation">
    <div class="container">
      <div class="navbar-brand">
        <nuxt-link class="navbar-item" to="/">
          <img src="https://www.tribuneo.id/img/logo/logo2.png">
        </nuxt-link>

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
            <nuxt-link to="/" class="navbar-item">Production</nuxt-link>
            <nuxt-link to="/blog" class="navbar-item">Services</nuxt-link>
            |
            <a href="https://instagram.com/tribuneo_medan" class="navbar-item">
              <img src="@/assets/instagram.png" alt="">
            </a>
            <a href="https://www.facebook.com/Tribuneomedan/" class="navbar-item">
              <img src="@/assets/facebook.png" alt="">
            </a>
            <a href="https://www.youtube.com/channel/UCEd48r04WN4s7Igkav_41eA" class="navbar-item">
              <img src="@/assets/youtube.png" alt="">
            </a>
            </div>
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
