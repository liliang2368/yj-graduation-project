<template>
  <div class="main-box">
    <div class="logo">
      <img src="../../assets/imges/logo.jpg" alt="">
    </div>
    <div class="sign">
      <div class="title"><span>注 册</span></div>
      <div class="sign-inform">
        <el-input
          prefix-icon="el-icon-user"
          size="large"
          placeholder="请输入用户名"
          v-model="username"
          clearable>
        </el-input>
        <el-input
          prefix-icon="el-icon-mobile-phone"
          size="large"
          placeholder="请输入手机号"
          v-model="phone"
          class="sign-input"
          clearable>
        </el-input>
        <el-input
          prefix-icon="el-icon-key"
          size="large"
          placeholder="请输入验证码"
          v-model="code"
          class="sign-input"
          clearable>
          <template slot="append"><el-button type="info"  @click="getCode" :style="{color:color}" :disabled="flag">{{text}}</el-button></template>
        </el-input>
        <el-input
          prefix-icon="el-icon-lock"
          size="large"
          placeholder="请输入密码"
          v-model="password"
          class="sign-input"
          clearable>
        </el-input>
        <el-button type="info" class="sign-btn" @click="toLogin">注册</el-button>
        <div class="tips">
          <span>已有账号？<a @click="toSign">立即登录</a></span>
        </div>
      </div>
    </div>
    <div class="img">
      <div class="connect">
        <img src="../../assets/imges/fx1.png" alt="" @mouseover="show2=!show2" @mouseout="show2=!show2">
        <img src="../../assets/imges/fx3.png" alt="">
        <img src="../../assets/imges/fx4.png" alt="">
      </div>
      <transition name="el-zoom-in-center">
        <div v-show="show2" class="transition-box"><img src="../../assets/imges/erweima.png" alt=""></div>
      </transition>
    </div>
  </div>
</template>

<script>
  export default {
    name: 'sign',
    data(){
      return {
        username:'',
        phone:'',
        code:'',
        password:'',
        text:'| 获取验证码',
        color:'#42b983',
        show2:false,
        flag:false
      }
    },
    methods:{
      toLogin(){
        if (this.username==''){
          this.$message({
            message: '请输入用户名！',
            type: 'warning'
          });
          return
        }
        if (this.phone==''){
          this.$message({
            message: '请输入手机号码！',
            type: 'warning'
          });
          return
        }
        if(!(/^1[3456789]\d{9}$/.test(this.phone))){
          this.$message.error('请输入正确格式的手机号！');
          return
        }
        if (this.password==''){
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
          this.$router.push({ name: 'login', params: { username:this.username,password:this.password}});
        }, 2000);
      },
      toSign(){
        this.$router.push({ path: '/login'});
      },
      getCode(){
        var that=this;
        var time=10;
        var timer=setInterval(function () {
          that.flag=true;
          that.color='#42b983';
          that.text='剩余'+time+'s';
          time--;
          if (time==0){
            that.flag=false;
            clearInterval(timer);
            that.color='#F56C6C';
            that.text='没有获取到？重新获取';
          }
        },1000)
      }
    }
  }
</script>

<style scoped>
  .main-box {
    position: relative;
  }

  .logo {
    margin: auto;
    width: 95%;
    height: 60px;
    border-bottom: 2px solid #E1E5EE;
  }
  .logo img{
    width:50px;
    height:50px;
    margin-top:5px;
    margin-left:150px;
  }

  .sign {
    top: 100px;
    left: 750px;
    position: absolute;
    z-index: 100;
    width: 500px;
    height: 700px;
    margin: auto;
    background: #fff;
    box-shadow: #d4d2d2 0px 0px 30px;
    -webkit-box-shadow: #d4d2d2 0px 0px 30px;
    -moz-box-shadow: #d4d2d2 0px 0px 30px;
  }

  .title {
    width: 80%;
    height: 50px;
    margin: auto;
    text-align: center;
    font-size: 35px;
    margin-top: 20px;
    color: #B0BCDC;
  }

  .sign-inform {
    width: 80%;
    margin: auto;
    margin-top: 50px;
  }

  .sign-input {
    margin-top: 50px;
  }
  .sign-btn{
    margin-top:50px;
    width:100%;
  }
  .tips{
    margin:auto;
    margin-top:50px;
    width:100%;
    text-align:center;
    color: #cccccc;
    font-size:15px;
  }
  .tips a{
    color: #67C23A;
  }
  .img {
    opacity: 0.5;
    top: 550px;
    position: absolute;
    width: 100%;
    height: 350px;
    background-image: url("../../assets/imges/sign.jpg");
  }
  .connect{
    position:absolute;
    right:20px;
    bottom:30px;
  }
  .connect img{
    opacity:1;
    margin-right:10px;
  }
  .transition-box {
    position:absolute;
    right:120px;
    bottom:65px;
  }

</style>
