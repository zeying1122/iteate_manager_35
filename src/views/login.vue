<template>
<div class="login">
    <div class="container">
        <img src="../assets/avatar.jpg" alt="" class="avatar">
    <el-form :model="loginForm" :rules="rules" ref="loginForm" class="demo-ruleForm">
  <el-form-item prop="username">
    <el-input v-model="loginForm.username" placeholder="请输入用户名"  prefix-icon="myicon-user"></el-input>
  </el-form-item>
    <el-form-item prop="password">
    <el-input v-model="loginForm.password" placeholder="请输入密码" prefix-icon="myicon-key"></el-input>
  </el-form-item>
  <el-form-item>
    <el-button type="primary" class="login-btn" @click='login'>登录</el-button>
  </el-form-item>
</el-form>
</div>
</div>
</template>
<script>
export default {
  data () {
    return {
      loginForm: {
        username: '',
        password: ''
      },
      rules: {
        username: [
          // required:必填,不能为空
          // trigger:什么时候出发这个验证规则
          // message:如果不符合验证规则是的提示信息
          { required: true, message: '请输入用户名', trigger: 'blur' }
        ],
        password: [
          { required: true, message: '请输入密码', trigger: 'blur' }
        ]
      }
    }
  },
  methods: {
    login () {
      this.$refs.loginForm.validate((valid) => {
        if (valid) {
          console.log('可以发请求啦')
        } else {
        //   this.$message({
        //     // 提示信息
        //     message: '请输入所有必填数据',
        //     // 提示类型:success,info,error,warning
        //     type: 'warning'
        //   })
          this.$message.warning('请输入所有必填数据')
          return false
        }
      })
    }
  }
}
</script>
<style lang="less" scoped>
.login {
  position: fixed;
  width: 100%;
  height: 100%;
  background-color: #2f4050;
  .container {
    position: absolute;
    left: 0;
    right: 0;
    width: 400px;
    padding: 0px 40px 15px 40px;
    margin: 200px auto;
    background: white;
    .avatar {
      position: relative;
      left: 50%;
      width: 120px;
      height: 120px;
      margin-left: -60px;
      margin-top: -60px;
      box-sizing: border-box;
      border-radius: 50%;
      border: 10px solid #fff;
      box-shadow: 0 1px 5px #ccc;
      overflow: hidden;
    }
    .login-btn {
      width: 100%;
    }
  }
}
</style>
