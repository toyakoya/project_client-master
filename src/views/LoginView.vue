<template>
  <div>
    <el-form :rules="rules" ref="loginForm" :model="user" class="loginContainer">
      <div class="title-container">
        <h3 class="title">后台管理系统</h3>
      </div>

      <el-form-item prop="username">
        <el-input
            ref="username"
            prefix-icon="el-icon-user"
            v-model="user.username"
            placeholder="请输入用户名"
            name="username"
            type="text"
            tabindex="1"
            auto-complete="on"
        />
      </el-form-item>

      <el-form-item prop="password">
        <el-input
            type="password"
            prefix-icon="el-icon-lock"
            show-password
            name="password"
            v-model="user.password"
            placeholder="请输入密码" ></el-input>
      </el-form-item>
      <el-button type="primary" style="width:100%" @click="submitLogin">登录</el-button>
    </el-form>
  </div>
</template>

<script>
export default {
  name: "LoginView",
  data(){
    return{
      captchaUrl: "",
      user:{
        username: null,
        password: null
      },
      rules:{
        username:[{required:true,message:"请输入用户名",trigger:"blur"},{ min: 5, max: 14, message: '长度在 5 到 14 个字符', trigger: 'blur' }
        ],
        password:[{required:true,message:"请输入密码",trigger:"blur"},{ min: 6,  message: '密码长度大于6', trigger: 'blur' }]
      }
    }
  },
  methods:{
    submitLogin(){
      console.log(this.user)
      this.$refs["loginForm"].validate((valid) => {
        if (valid) {  // 表单校验合法
          this.request.post('/user/login', this.user).then(res => {
            if( !res ){
              this.$message.error("用户名或密码错误")
            } else {
              this.$router.push("/")
            }
          })
        } else {  // 表单校验不合法
          console.log('error submit!!');
        }
      })
    }
  }
};
</script>

<style lang="less" scoped>
.loginContainer{
  //display: inline-block;
  overflow: hidden;
  //height: 47px;
  width: 85%;
  border-radius: 15px;
  background-clip: padding-box;
  margin: 180px auto;
  background-color: #2d3a4b;
  padding: 15px 35px 15px 35px;
  //background: aliceblue;
  //border:1px solid blueviolet;
  box-shadow: 0 0 25px #f885ff;
}

.title-container {
  position: relative;
  .title {
    font-size: 26px;
    color: #eee;
    margin: 0px auto 40px auto;
    text-align: center;
    font-weight: bold;
  }
}
.loginRemember{
  text-align: left;
  margin: 0px 0px 15px 0px;
}
body{
  background-color: #2d3a4b;
  //background-image: linear-gradient(to bottom right, #FC4668, #3F5EF8) ;
  background-size: 100%;
}
</style>