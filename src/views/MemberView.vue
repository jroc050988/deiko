<template>
  <div class="member">
    <div class="pagesZone">
      <h2 class="mainTitle">會員專區</h2>
      <div class="memberBox">
        <Sidebar />
        <div class="memberBox__content">
          <p class="aisatsu">Hi! {{memberName}}，歡迎回來!</p>
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
import axios from "axios";
export default {
  name: "MemberView",
  components: {
    Sidebar,
  },
  data() {
    return {
      memberName:"",
      loginId:"",
    };
  },
  mounted() {
    this.loginId = this.$cookies.get("loginId");
    this.getData();
  },
  methods: {
    getData() {
      axios
        .get(`http://localhost:3000/users/${this.loginId}`)
        .then((res) => {
          this.memberName = res.data.name;
        })
        .catch(function (error) {
          // 请求失败处理
          console.log(error);
        });
    }
  },
};
</script>