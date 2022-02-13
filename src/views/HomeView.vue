<template>
  <div class="home">
    <IxBanner />
    <img alt="Vue logo" src="../assets/images/logo.png" />
    <HelloWorld msg="Welcome to Your Vue.js App" />
  </div>
</template>

<script>
// @ is an alias to /src
import HelloWorld from "@/components/HelloWorld.vue";
import IxBanner from "@/components/IxBanner.vue";
export default {
  name: "HomeView",
  components: {
    HelloWorld,
    IxBanner,
  },
};
</script>
