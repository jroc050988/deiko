<template>
  <div class="member">
    <div class="pagesZone">
      <h2 class="mainTitle">會員專區</h2>
      <div class="memberBox">
        <Sidebar />
        <div class="memberBox__content">
          <p class="aisatsu">Hi! 狄哥，歡迎回來!</p>
          <div class="memberBox__inputBox">
            <div></div>
          </div>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
import Sidebar from "@/components/Sidebar.vue";
export default {
  name: "MemberView",
  components: {
    Sidebar,
  },
  data() {
    return {};
  },
  mounted() {},
  methods: {
    logout() {
      alert("帳號已登出");
      this.$cookies.remove("login");
      window.location.href = "./index.php";
    },
  },
};
</script>