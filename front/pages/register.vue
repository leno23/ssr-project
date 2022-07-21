<template>
  <div class="login-container">
    <el-form
    label-width="100px"
      class="login-form"
      :model="form"
      :rules="rules"
      ref="registerForm"
    >
    <div class="title-container">
      <img src="/logo.png" alt="">
    </div>
    <el-form-item props="email" label="邮箱">
      <el-input v-model="form.email" placeholder="亲输入邮箱"></el-input>
    </el-form-item>
    
    <el-form-item props="captcha" label="验证码" class="captcha-container">
      <el-input v-model="form.captcha" style="width:100px" placeholder="亲输入邮箱"></el-input>
      <img :src="code.captcha" @click="refreshCaptcha" alt="" class="captcha">
    </el-form-item>
    <el-form-item props="nickname" label="昵称">
      <el-input v-model="form.email" placeholder="亲输入昵称"></el-input>
    </el-form-item>
    <el-form-item props="passwd" label="昵称">
      <el-input v-model="form.email" placeholder="请输入密码"></el-input>
    </el-form-item>
    <el-form-item props="repasswd" label="昵称">
      <el-input v-model="form.email" placeholder="请在再次输入密码"></el-input>
    </el-form-item>
    <el-form-item>
      <el-button>注册</el-button>
    </el-form-item>
    </el-form>
  </div>
</template>

<script>
export default {
  data(){
    return {
      form:{
        email:'',
        nickname:'',
        passwd:'',
        repasswd:''
      },
      rules:{
        email:[
          {required:true,message:'请输入邮箱'},
          {type:'email',message:'请输入正确的邮箱格式'}
        ]
      },
      code:{
        captcha:'/api/captcha'
      }
    }
  },
  methods:{
    refreshCaptcha(){
      this.code.captcha =  '/api/captcha?' + Date.now()
    }
  }
};
</script>

<style lang="stylus">
  .login-container
    width 50%
    margin 0 auto
    .captcha
      display inline-block
      vertical-align top
      cursor pointer
</style>
