<template>
  <div class="member_pofile">
    <div class="pagesZone">
      <div class="memberBox">
        <Sidebar />
        <div class="memberBox__content">
          <h2 class="mainTitle">會員資料</h2>
          <p class="mainText">為保障您的權益，請正確填寫您的個人信息</p>
          <div class="memberBox__inputBox">
            <div class="memberBox__input">
              <label for="name">電子信箱</label>
              <input id="name" type="text" v-model="memberEmail" disabled />
            </div>
            <div class="memberBox__input">
              <label for="name">姓名</label>
              <input id="name" type="text" value="" v-model="memberName" />
            </div>
            <!-- <div class="memberBox__input">
              <label for="name">生日</label>
              <input id="name" type="text" value="123" />
            </div>
            <div class="memberBox__input">
              <label for="name">連絡電話</label>
              <input id="name" type="text" value="123" />
            </div> -->
            <div class="btnBox btnstyle--1">
              <a href="" tittle="送出" @click="patchData();">送出</a>
            </div>
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
  name: "Member_pofileView",
  components: {
    Sidebar,
  },
  data() {
    return {
      memberName: "",
      loginId: "",
      memberEmail:""
    };
  },
  mounted() {
    this.loginId = this.$cookies.get("loginId");
    console.log(this.$cookies.get("loginId"));
    this.getData();
    
  },
  methods: {
    patchData() {
      axios
        .patch(`http://localhost:3000/users/${this.loginId}`, {
          name: this.memberName
        })
        .then((res) => {
          console.log(res.data.id);
          
        })
        .catch(function (error) {
          // 请求失败处理
          console.log(error);
        });
    },
    getData() {
      axios
        .get(`http://localhost:3000/users/${this.loginId}`)
        .then((res) => {
          this.memberEmail = res.data.id;
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