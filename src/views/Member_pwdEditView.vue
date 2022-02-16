<template>
  <div class="member_pwdEdit">
    <div class="pagesZone">
      <div class="memberBox">
        <Sidebar />
        <div class="memberBox__content">
          <h2 class="mainTitle">會員資料</h2>
          <p class="mainText">為保障您的權益，請正確填寫您的個人信息</p>
          <div class="memberBox__inputBox">
            <div class="memberBox__input">
              <input
                id="name"
                type="text"
                v-model="yourpassword"
                placeholder="請輸入當前密碼"
              />
            </div>
            <PasswordConfirm />
            <div class="btnBox btnstyle--1">
              <a href="" tittle="送出" @click="patchData()">送出</a>
            </div>
          </div>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
import Sidebar from "@/components/Sidebar.vue";
import PasswordConfirm from "@/components/PasswordConfirm.vue";
// import axios from "axios";
export default {
  name: "Member_pwdEditView",
  components: {
    Sidebar,
    PasswordConfirm,
  }
  
};
</script>