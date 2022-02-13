<template>
  <header>
    <h1>
      <router-link to="/">
        <img src="../assets/images/logo.svg" alt="狄哥豬排" />
      </router-link>
    </h1>
    <div class="header__nav">
      <nav>
        <ul class="header-menu">
          <li>
            <router-link to="/about">
              <i class="fas fa-hippo"></i>關於狄哥
            </router-link>
          </li>
          <li>
            <router-link to="/about">
              <i class="fas fa-receipt"></i>我要點餐
            </router-link>
          </li>
          <li>
            <router-link to="/about">
              <i class="fas fa-utensils"></i>線上菜單
            </router-link>
          </li>
          <li>
            <router-link to="/about">
              <i class="far fa-building"></i>分店資訊
            </router-link>
          </li>
          <li>
            <router-link to="/about">
              <i class="far fa-envelope-open"></i>聯絡我們
            </router-link>
          </li>
        </ul>
      </nav>
      <!-- <div class="lang">
        <a href="#" title="選擇語言">繁體中文</a>
      </div> -->
      <div class="order btnstyle">
        <router-link to="/" :href="url" :tittle="text" v-text="text">
          <i class="fas fa-user"></i>
        </router-link>
        <div class="btn--hover">
          <router-link to="/" :href="url" :tittle="text" v-text="text">
            <i class="fas fa-user"></i>
          </router-link>
        </div>
      </div>
    </div>
  </header>
</template>
<script>
export default {
  name: "HeaderNav",
  data() {
    return {
      url: "/login",
      text: "會員登入",
    };
  },
  mounted() {
    if (this.$cookies.get("login") == "istrue") {
      console.log("會員已登入");
      this.url = "/member";
      this.text = "會員專區";
    }
  },
  methods: {},
};
</script>