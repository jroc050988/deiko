<template>
  <div class="passwordConfirm">
    <div class="loginBox__input">
      <label>
        <input
          :type="isView01"
          name=""
          id=""
          placeholder="設定密碼"
          v-model="yourNewpassword"
          @keyup="validation_password()"
          onkeyup="value=value.replace(/[^a-zA-Z0-9]/g,'')"
          onpaste="return false"
          oncontextmenu="return false"
        />
        <i @click.stop="eye01()" :class="eyeIcon01"></i>
        <ul class="passwordRule__list">
          <li>
            <span class="passwordRule" :class="{ green: isRule02_true }"
              ><i class="checkicon far fa-check-circle"></i> 6~12個字元</span
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
          ><i class="checkicon far fa-check-circle"></i> 確認密碼正確</span
        >
      </label>
    </div>
  </div>
</template>

<script>
export default {
    name: "PasswordConfirm",
    data() {
    return {
      yourpassword: "",
      yourNewpassword: "",
      yourNewpassword_confirm: "",
      loginId: "",
      isRule02_true: false,
      isRule03_true: false,
      isRule04_true: false,
      isRule05_true: false,
    };
  },
  mounted() {
    this.loginId = this.$cookies.get("loginId");
  },
  methods: {
    validation_password() {
      this.isOk02 = false;
      this.isRule02_true = false;
      this.isRule03_true = false;
      this.isRule04_true = false;
      var pwdLen = this.yourNewpassword.length;
      // console.log(pwdLen);
      if (pwdLen < 6 || pwdLen > 12) {
        // console.log(pwdLen);
        console.log("請輸入6~12個字元");
        return;
      } else {
        console.log("長度正常");
        this.isRule02_true = true;
        if (
          /[a-z]/.test(this.yourNewpassword) == false ||
          /[0-9]/.test(this.yourNewpassword) == false
        ) {
          console.log("請包含英文及數字");
          return;
        } else {
          console.log("已包含英文及數字");
          this.isRule03_true = true;
          if (/[A-Z]/.test(this.yourNewpassword) == false) {
            console.log("未包含大寫字母");
            return;
          } else {
            this.isRule04_true = true;
            console.log("已包含大寫字母");
            this.isOk02 = true;
          }
        }
      }
    },
    validation_password_confirm() {
      this.isOk03 = false;
      this.isRule05_true = false;
      if (this.yourNewpassword !== this.yourPassword02) {
        console.log("確認密碼錯誤");
      } else {
        console.log("確認密碼正確");
        this.isRule05_true = true;
        this.isOk03 = true;
      }
    },
  },
}
</script>