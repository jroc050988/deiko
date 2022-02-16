<template>
  <aside class="sidebar">
    <ul class="sidebar__list">
      <li class="sidebar__item">
        <router-link to="/member_pofile" tittle="會員資料">
          <i class="fas fa-user-edit"></i> 會員資料
        </router-link>
      </li>
      <li class="sidebar__item">
        <a href="#" title="會員紅利"><i class="fas fa-donate"></i> 會員紅利</a>
      </li>
      <li class="sidebar__item">
        <a href="#" title="專屬優惠"
          ><i class="fas fa-ticket-alt"></i> 專屬優惠</a
        >
      </li>
      <li class="sidebar__item">
        <router-link to="/member_pwdEdit" tittle="修改密碼">
          <i class="fas fa-user-edit"></i> 修改密碼
        </router-link>
      </li>
      <li class="sidebar__item">
        <a
          v-on:click.prevent="logout()"
          href="#"
          title="登出"
          class="sidebar__item--logout"
          >登出</a
        >
      </li>
    </ul>
  </aside>
</template>

<script>
export default {
  name: "Sidebar",
  data() {
    return {};
  },
  mounted() {},
  methods: {
    logout() {
      alert("帳號已登出");
      this.$cookies.remove("login");
      this.$cookies.remove("loginId");
      window.location.href = "/";
    },
  },
};
</script>