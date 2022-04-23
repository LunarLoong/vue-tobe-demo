<template>
  <div class="login-container">
    <div class="login-box">
      <el-form label-width="0px" ref="loginForm" class="login-form" :model="loginForm" :rules="passRules">
        <el-form-item prop="username">
          <el-input type="text" prefix-icon="el-icon-user" v-model="loginForm.username"
                    placeholder="请输入用户名..."></el-input>
        </el-form-item>
        <el-form-item prop="password">
          <el-input type="password" prefix-icon="el-icon-lock" v-model="loginForm.password"
                    placeholder="请输入密码..."></el-input>
        </el-form-item>
        <el-form-item>
          <el-button type="primary" @click="login">登录</el-button>
          <el-button @click="reset">重置</el-button>
        </el-form-item>
      </el-form>
    </div>
  </div>
</template>

<script>
export default {
  name: 'Login',
  data () {
    return {
      loginForm: {
        username: '',
        password: ''
      },
      passRules: {
        username: [
          {
            required: true,
            message: '请输入用户名',
            trigger: 'blur'
          },
          {
            min: 3,
            max: 8,
            message: '长度在 3 到 8 个字符',
            trigger: 'blur'
          }
        ],
        password: [
          {
            required: true,
            message: '请输入密码',
            trigger: 'blur'
          },
          {
            min: 6,
            max: 16,
            message: '长度在 6 到 16 个字符',
            trigger: 'blur'
          }
        ]
      }
    }
  },
  methods: {
    login () {
      this.$refs.loginForm.validate((valid) => {
        if (valid === true) {
          if (this.loginForm.username === 'admin' && this.loginForm.password === '123456') {
            this.$message({
              type: 'success',
              message: '登陆成功'
            })
            this.$router.push('/home')
          } else {
            this.$message({
              type: 'error',
              message: '用户名或密码错误'
            })
          }
        } else {
          this.$message({
            type: 'error',
            message: '参数不合法'
          })
        }
      })
    },
    reset () {
      this.$refs.loginForm.resetFields()
      this.$message({
        type: 'info',
        message: '已重置'
      })
    }
  }
}
</script>

<style scoped>
.login-container {
  width: 100%;
  height: 100%;
  position: relative;
  background: linear-gradient(to right, #4ca2cd, #67B26F);
}

.login-box {
  width: 450px;
  height: 300px;
  background-color: #fff;
  border-radius: 5px;
  position: absolute;
  left: 50%;
  top: 50%;
  transform: translate(-50%, -50%);
}

.login-box::before {
  content: '';
  width: 130px;
  height: 130px;
  background: #ddd;
  box-shadow: 0 0 8px #7e7e7e;
  border-radius: 50%;
  position: absolute;
  top: 0;
  left: 50%;
  transform: translate(-50%, -50%);
}

.login-box::after {
  content: '';
  content: '';
  width: 120px;
  height: 120px;
  background: url("./assets/logo.png") no-repeat center center;
  border-radius: 50%;
  border: 8px solid #fff;
  position: absolute;
  top: 0;
  left: 50%;
  transform: translate(-50%, -50%);
}

.login-form {
  width: 85%;
  position: relative;
  top: 70%;
  left: 50%;
  transform: translate(-50%, -70%);
  text-align: center;
}
</style>
