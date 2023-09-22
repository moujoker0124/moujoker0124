- 👋 Hi, I’m 2023
- 👀 I’m interested in ...
- 🌱 I’m currently learning ...
- 💞️ I’m looking to collaborate on ...
- 📫 How to reach me ...
mougg is me
<!---
moujoker0124/moujoker0124 is a ✨ special ✨ repository because its `README.md` (this file) appears on your GitHub profile.
You can click the Preview link to take a look at your changes.
<template>
  <div class="login_container">
    <el-row>
      <el-col :span="12" :xs="0"></el-col>
      <el-col :span="12" :xs="24">
        <el-form :model="loginForm" :rules="rules" class="login_form">
          <h1>Hello</h1>
          <h2>欢迎来到甄选后台</h2>
          <el-form-item>
            <el-input
              placeholder="请输入用户名"
              :prefix-icon="User"
              v-model="loginForm.username"
            ></el-input>
          </el-form-item>
          <el-form-item>
            <el-input
              placeholder="请输入密码"
              type="password"
              :prefix-icon="Lock"
              v-model="loginForm.password"
              show-password
            ></el-input>
          </el-form-item>
          <el-form-item>
            <el-button
              :loading="loading"
              class="lgoin_btn"
              type="primary"
              round
              @click="login"
              >登录</el-button
            >
          </el-form-item>
        </el-form>
      </el-col>
    </el-row>
  </div>
</template>
<script setup lang="ts">
import { User, Lock } from "@element-plus/icons-vue/global";
import { reactive, ref } from "vue";
import { useRouter } from "vue-router";
import { ElNotification } from "element-plus";
//导入用户相关小仓库
import useUserStore from "@/store/modules/user";
//引入获取当前时间的方法
import { getTime } from "@/utils/time.ts";
let userStore = useUserStore();
//   console.log(userStore);
//   console.log(loginForm);
// 获取路由器
let $router = useRouter();
//收集账号密码
const loginForm = reactive({
  username: "admin",
  password: "111111",
});
//定义变量控制按钮加载效果
let loading = ref(false);
//登录按钮回调
const login = async () => {
  loading.value = true;
  //登录成功后跳转到首页
  try {
    await userStore.userLogin(loginForm);
    loading.value = false;
    $router.push({ path: "/" });
    ElNotification({
      title: "登录成功",
      message: `HI,${getTime()}!欢迎回来`,
      type: "success",
    });
  } catch (err) {
    console.log(err);
    loading.value = false;
    ElNotification({
      title: "登录失败",
      message: (err as Error).message,
      type: "error",
    });
  }
  // router.push({path:'/home'})
};
//定义表单校验需要的配置对象
const rules = {
  username: [
    { required: true, message: "请输入用户名", trigger: "blur" },
    {
      pattern: /^[a-zA-Z0-9_-]{4,16}$/,
      message: "用户名必须是4-16位字母数字下划线组合",
      trigger: "blur",
    },
  ],
  password: [
    { required: true, message: "请输入密码", trigger: "blur" },
    {
      pattern: /^[a-zA-Z0-9_-]{4,16}$/,
      message: "密码必须是4-16位字母数字下划线组合",
      trigger: "blur",
    },
  ],
};
</script>
<style scoped lang="scss">
.login_container {
  width: 100%;
  height: 100vh;
  background-color: #f5f5f5;
  background: url("@/assets/images/background.jpg") no-repeat;
  background-size: cover;
}
.login_form {
  position: relative;
  width: 80%;
  top: 30vh;
  background: url("@/assets/images/login_form.png") no-repeat;
  background-size: cover;
  h1 {
    text-align: center;
    font-size: 40px;
    color: #fff;
    margin-bottom: 20px;
  }
  h2 {
    text-align: center;
    font-size: 20px;
    color: #fff;
    margin: 20px;
  }
  .lgoin_btn {
    width: 100%;
    margin-top: 20px;
  }
}
</style>

--->
