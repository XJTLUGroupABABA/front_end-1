<script src="https://cdn.jsdelivr.net/npm/vue/dist/vue.js"></script> 

<template>
  <div class="container">
    <div class="background"></div>
    <div class="contain">
      <a class="title"> GIFTER SYSTEM REGISTER </a>

      <div class="form">
        <input
          type="text"
          v-model.trim="name"
          placeholder="Please enter your user name"
          onKeyUp="value=value.replace(/[\W]/g,'')"
        /><br />
      </div>
      <div class="form">
        <input
          type="password"
          v-model.trim="password"
          placeholder="Please enter your password"
        /><br />
      </div>
      <div class="form">
        <input
          type="password"
          v-model.trim="passwordAgain"
          placeholder="Please enter the password again"
        /><br />
      </div>
      <div class="form">
        <input
          type="email"
          v-model.trim="phone"
          placeholder="Please enter your registration phone"
        /><br />
      </div>
      <button @click.prevent="handlefinish">REGISTER</button>
    </div>
  </div>
</template>

<style scoped>
.container {
  height: 900px;
  width: 100%;
}
.background {
  background: url("../assets/gift.jpg") no-repeat center;
  float: left;
  width: 100%;
  height: 900px;
  background-repeat: no-repeat;
  background-size: cover;
  -webkit-filter: blur(5px) !important;
  -moz-filter: blur(5px) !important;
  -o-filter: blur(5px) !important;
  -ms-filter: blur(5px) !important;
  filter: blur(4px) !important;
  text-align: center;
}
.contain {
  position: absolute;
  width: 500px;
  height: 500px;
  margin-top: 200px;
  margin-left: 500px;
  /* background-color: royalblue; */
  z-index: 5;
}
.title {
  color: rgba(255, 255, 255, 100);
  font-size: 30px;
  text-align: left;
  font-family: SourceHanSansSC-regular;
  text-align: center;
  padding-left: 7%;
}

input {
  outline-style: none;
  border: 0px;
  width: 440px;
  border-radius: 30px;
  height: 50px;
  padding: 25px;
  margin-top: 40px;
  border: 1px solid rgba(255, 255, 255, 100);
  opacity: 0.4;
  background-color: rgba(255, 255, 255, 100);
}
input::-webkit-input-placeholder {
  color: rgb(27, 27, 27);
}
input::-moz-input-placeholder {
  color: rgb(27, 27, 27);
}
input::-ms-input-placeholder {
  color: rgb(27, 27, 27);
}

button {
  left: 623px;
  top: 682px;
  width: 120px;
  height: 50px;
  line-height: 26px;
  border-radius: 30px;
  margin-top:40px;
  background-color: rgba(210, 111, 108, 100);
  color: rgba(255, 255, 255, 100);
  font-size: 18px;
  text-align: center;
  font-family: Roboto;
  border: 1px solid rgba(210, 111, 108, 100);
  margin-left:30%;
}
</style>

<script>
export default {
  name: "Register",
  props: {
    msg: String,
  },
  data() {
    return {
      name: "",
      password: "",
      passwordAgain: "",
      phone: "",
    };
  },
  methods: {
    //点击完成按钮触发handlefinish
    handlefinish: function () {
      if (localStorage["name"] === this.name) {
        alert("用户名已存在"); //如果用户名已存在则无法注册
      } else if (this.name === "") {
        alert("用户名不能为空");
      }
      else if (this.name == "this.value=this.value.replace(/[^\u4e00-\u9fa5]/g,'')") {
        alert("用户名不能为中文");
      }
      else {
        //将新用户信息存储到localStorage
        localStorage.setItem("name", this.name);
        localStorage.setItem("password", this.password);
        localStorage.setItem("mail", this.passwordAgain);
        localStorage.setItem("tel", this.phone);
        localStorage.setItem("s", "false");
        alert("注册成功");
        this.$router.replace("/page_contact"); //完成注册后跳转至contact页面
      }
    },
  },
};
</script>


