<template>
    <div class="main-box">
      <div class="login-img">
        <img src="../assets/imges/1597976515_WPS图片.jpg" alt="">
      </div>
      <div class="login-form">
        <div class="login-box">
          <div class="title"><span>LOGIN</span></div>
          <div class="tips"><span>Login with your account</span></div>
          <div class="login-infor">
            <el-input
              class="username"
              placeholder="User name"
              v-model="userName"
              prefix-icon="el-icon-user-solid"
              clearable>
            </el-input>
            <el-input placeholder="Password" v-model="password" prefix-icon="el-icon-lock"   show-password></el-input>
          </div>
          <div class="retrieve-password">
<!--            <el-radio  v-model="radio" label="1" @change="remeber" >备选项</el-radio>-->
            <span>Forgot Password?</span>
          </div>
          <el-button class="login-btn" @click="toLogin">Login</el-button>
          <div class="sign"><span>if you do not have account,</span ><span @click="toSign">Sign up</span></div>
        </div>
      </div>
    </div>
</template>

<script>
  export default {
    name: 'login',
    data () {
      return {
        userName:'',
        password:'',
        radio: ''
      }
    },
    mounted () {
      this.userName=this.$route.params.username;
      this.password=this.$route.params.password;
    },
    methods:{
      toLogin(){
        if (!this.userName||this.userName==''){
          this.$message({
            message: '请输入账号！',
            type: 'warning'
          });
          return
        }
        if (!this.password||this.password==''){
          this.$message({
            message: '请输入密码！',
            type: 'warning'
          });
          return
        }
        const loading = this.$loading({
          lock: true,
          text: 'Login',
          spinner: 'el-icon-loading',
          background: 'rgba(0, 0, 0, 0.7)'
        });
        setTimeout(() => {
          loading.close();
          this.$router.push({ path: '/yjshopping'});

        }, 2000);
      },
      toSign(){
        this.$router.push({ path: '/sign'});
      }
    }
  }

</script>
<style scoped>
  .main-box{
    position:relative;
  }
  .login-img{
    position:absolute;
    left:0;
    width:1119px;
    height:944px;
  }
  .login-img img{
    width:100%;
    height:100%;
  }
  .login-form{
    width:780px;
    height:944px;
    position:absolute;
    right:0;
  }
  .login-box{
    width:500px;
    margin: auto;
  }
  .title{
    width:150px;
    height:35px;
    font-size:30px;
    margin:auto;
    margin-top:150px;
  }
  .tips{
    margin-top:50px;
    font-size:20px;
    color: #767676;
  }
  .login-infor{
    margin-top:50px;
  }
  .username{
    margin-bottom:50px;
    width:500px;
  }
  .retrieve-password{
    width:500px;
    margin-top:15px;
    text-align:right;
    color:#B0BCDC;
    font-size:20px;

  }
  .login-btn{
    margin-top:40px;
    width:100%;
    height:50px;
    border:1px solid #B0BCDC;
    color:#B0BCDC;
  }
  .sign{
    margin-top:80px;
    width:500px;
    text-align:center;
    color:#B2B2B2;
    font-size:18px;
  }
  .sign span:nth-child(2){
    text-decoration:underline
  }
</style>
