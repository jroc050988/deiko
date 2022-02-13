<template>
  <div id="app">
    <div class="warp">
      <HeaderNav />

      <router-view />
      <Footer />
    </div>
  </div>
</template>
<script>
import HeaderNav from "./components/HeaderNav.vue";
import Footer from "./components/Footer.vue";

export default {
  name: "App",
  components: {
    HeaderNav,
    Footer,

  },
};
</script>

<style lang="scss">
@import "assets/scss/style.scss";
</style>
