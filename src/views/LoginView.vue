<template>
  <div class="login">
    <div class="pagesZone">
      <h2 class="mainTitle">會員登入</h2>
      <div class="loginBox">
        <form action="" method="" class="loginBox__inputBox">
          <div class="loginBox__input">
            <label>
              <input
                type="email"
                name=""
                id=""
                placeholder="電子信箱"
                v-model="yourEmail"
              />
            </label>
          </div>
          <div class="loginBox__input">
            <label>
              <input
                :type="isView"
                name=""
                id=""
                placeholder="密碼"
                v-model="yourPassword"
              />
              <i @click="eye()" :class="eyeIcon"></i>
            </label>
          </div>
          <a href="" title="忘記密碼" class="loginBox__forget"
            >忘記密碼 <i class="fas fa-question"></i
          ></a>
          <div class="loginBox__btnBox btnstyle--1">
            <a href="" tittle="送出" @click.prevent="submit()">送出</a>
          </div>
          <a href="signup.php" title="註冊會員" class="loginBox__signin"
            >您還沒有會員嗎? 立即註冊</a
          >
        </form>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: "LoginView",
  data() {
    return {
      yourEmail: "",
      yourPassword: "",
      isView: "password",
      eyeIcon: "eyeicon far fa-eye",
    };
  },
  mounted() {},
  methods: {
    getData() {
      axios
        .get(
          `http://localhost:3000/users?id=${this.yourEmail}&password=${this.yourPassword}`
        )
        .then((res) => {
          if (res.data.length == 0) {
            alert("帳號/密碼輸入錯誤");
          } else {
            alert("登入成功");
            this.$cookies.set("login", "istrue", 60 * 60 * 2);
            window.location.href = "./index.php";
          }
        })
        .catch(function (error) {
          // 请求失败处理
          console.log(error);
        });
    },
    submit() {
      this.getData();
    },
    eye() {
      if (this.isView == "password") {
        this.isView = "text";
        this.eyeIcon = "eyeicon far fa-eye-slash";
      } else {
        this.isView = "password";
        this.eyeIcon = "eyeicon far fa-eye";
      }
    },
  },
};
</script>


