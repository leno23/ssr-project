<template>
  <div class='container'>
    <el-form  style="width:400px;" label-width='100px' :rules='rules' ref='formRef'>
      <el-form-item label='用户名'>
        <el-input v-model='formData.username'></el-input>
      </el-form-item>
      <el-form-item label='密码'>
        <el-input type='password' v-model='formData.password'></el-input>
      </el-form-item>
      <el-form-item label='验证码'>
        <el-input v-model='formData.captcha' style='width:70px;'></el-input>
        <img class='captcha' :src="imgUrl" alt="" @click='getUrl'>
      </el-form-item>
      <el-form-item>
        <el-button size='small' type='primary'>登录</el-button>
      </el-form-item>
      
    </el-form>
  </div>
</template>

<script lang="ts">
import Vue from 'vue'

export default Vue.extend({
  name: 'IndexPage',
  data() {
    return {
      imgUrl: '/api/captcha?' + Date.now(),
      formData: {
        username:'',
        password:'',
        captcha: ''
      },
      rules:{
        username:[{required:true,trigger:'blur'}]
      }
    }
  },
  methods: {
    getUrl() {
      this.imgUrl = '/api/captcha?' + Date.now()
    }
  }
})
</script>
<style lang='stylus'>
.container
  padding:10px
.captcha
  display: inline-block;
  vertical-align: top;
</style>
