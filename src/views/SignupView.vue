<template>
  <div class="signup">
    <div class="pagesZone">
      <h2 class="mainTitle">會員註冊</h2>
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
                @blur="getData()"
              />
              <span class="passwordTip"
                >為日後驗證信箱，請輸入正確的電子信箱</span
              ><br />
              <span class="passwordRule" :class="{ green: isRule01_true }"
                ><i class="checkicon far fa-check-circle"></i>
                可使用此電子信箱</span
              >
            </label>
          </div>
          <div class="loginBox__input">
            <label>
              <input
                :type="isView01"
                name=""
                id=""
                placeholder="設定密碼"
                v-model="yourPassword01"
                @keyup="validation_password()"
                onkeyup="value=value.replace(/[^a-zA-Z0-9]/g,'')"
                onpaste="return false"
                oncontextmenu="return false"
              />
              <i @click.stop="eye01()" :class="eyeIcon01"></i>
              <ul class="passwordRule__list">
                <li>
                  <span class="passwordRule" :class="{ green: isRule02_true }"
                    ><i class="checkicon far fa-check-circle"></i>
                    6~12個字元</span
                  >
                </li>
                <li>
                  <span class="passwordRule" :class="{ green: isRule03_true }"
                    ><i class="checkicon far fa-check-circle"></i>
                    密碼包含英文字母及數字</span
                  >
                </li>
                <li>
                  <span class="passwordRule" :class="{ green: isRule04_true }"
                    ><i class="checkicon far fa-check-circle"></i>
                    至少包含一個大寫英文字母</span
                  >
                </li>
              </ul>
            </label>
          </div>
          <div class="loginBox__input">
            <label>
              <input
                :type="isView02"
                name=""
                id=""
                placeholder="確認密碼"
                v-model="yourPassword02"
                @keyup="validation_password_confirm()"
                onpaste="return false"
                oncontextmenu="return false"
              />
              <i @click.stop="eye02()" :class="eyeIcon02"></i>
              <span class="passwordTip">請再次輸入您設定的密碼</span><br />
              <span class="passwordRule" :class="{ green: isRule05_true }"
                ><i class="checkicon far fa-check-circle"></i>
                確認密碼正確</span
              >
            </label>
          </div>
          <div class="loginBox__btnBox btnstyle--1">
            <a href="" tittle="送出" @click.prevent="submit()">送出</a>
          </div>
        </form>
      </div>
    </div>
  </div>
</template>

<script>
import axios from "axios";

export default {
  name: "SignupView",
  data() {
    return {
      yourEmail: "",
      yourPassword01: "",
      yourPassword02: "",
      isView01: "password",
      isView02: "password",
      eyeIcon01: "eyeicon far fa-eye",
      eyeIcon02: "eyeicon far fa-eye",
      isRule01_true: false,
      isRule02_true: false,
      isRule03_true: false,
      isRule04_true: false,
      isRule05_true: false,
      usersData: null,
    };
  },
  mounted() {},
  methods: {
    getData() {
      axios
        .get(`http://localhost:3000/users?id=${this.yourEmail}`)
        .then((res) => {
          console.log(res.data);
          this.usersData = res.data;
          this.validation_email();
        })
        .catch(function (error) {
          // 请求失败处理
          console.log(error);
        });
    },
    postData() {
      axios
        .post(`http://localhost:3000/users`, {
          id: this.yourEmail,
          password: this.yourPassword01,
        })
        .then(() => {
          console.log("ok");
          alert("註冊成功");
          window.location.href = "./login.php";
        })
        .catch(function (error) {
          // 请求失败处理
          console.log(error);
        });
    },
    validation_email() {
      console.log(/[@]/.test(this.yourEmail));
      if (this.usersData.length == 0 && /[@]/.test(this.yourEmail) == true) {
        console.log("可使用此電子信箱");
        this.isRule01_true = true;
      } else {
        console.log("此電子信箱已註冊");
        this.isRule01_true = false;
      }
    },
    validation_password() {
      var pwdLen = this.yourPassword01.length;
      // console.log(pwdLen);
      if (pwdLen < 6 || pwdLen > 12) {
        // console.log(pwdLen);
        console.log("請輸入6~12個字元");
        return;
      } else {
        console.log("長度正常");
        this.isRule02_true = true;
        if (
          /[a-z]/.test(this.yourPassword01) == false ||
          /[0-9]/.test(this.yourPassword01) == false
        ) {
          console.log("請包含英文及數字");
          return;
        } else {
          console.log("已包含英文及數字");
          this.isRule03_true = true;
          if (/[A-Z]/.test(this.yourPassword01) == false) {
            console.log("未包含大寫字母");
            return;
          } else {
            this.isRule04_true = true;
            console.log("已包含大寫字母");
          }
        }
      }
    },
    validation_password_confirm() {
      if (this.yourPassword01 !== this.yourPassword02) {
        console.log("確認密碼錯誤");
      } else {
        console.log("確認密碼正確");
        this.isRule05_true = true;
      }
    },
    submit() {
      this.postData();
    },
    eye01() {
      if (this.isView01 == "password") {
        this.isView01 = "text";
        this.eyeIcon01 = "eyeicon far fa-eye-slash";
      } else {
        this.isView01 = "password";
        this.eyeIcon01 = "eyeicon far fa-eye";
      }
    },
    eye02() {
      if (this.isView02 == "password") {
        this.isView02 = "text";
        this.eyeIcon02 = "eyeicon far fa-eye-slash";
      } else {
        this.isView02 = "password";
        this.eyeIcon02 = "eyeicon far fa-eye";
      }
    },
  },
};
</script>


