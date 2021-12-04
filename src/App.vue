<template>
  <div id="app">
    <div class="box">
      <video
        width="condition"
        type="video/mp4"
        autoplay="autoplay"
        loop="loop"
        muted="muted"
      >
        <source src="./assets/Skybg.webm" type="video/mp4" />
      </video>
    </div>

    <el-card class="box-login">
      <el-form
        ref="elForm"
        :model="formData"
        :rules="rules"
        size="medium"
        label-width="125px"
      >
        <div class="title-container">
          <h1 class="title">触光登录系统</h1>
        </div>

        <el-form-item label-width="0" prop="username">
          <el-input
            v-model="formData.username"
            placeholder="请输入用户名"
            clearable
            prefix-icon="iconfont icon-user"
          ></el-input>
        </el-form-item>

        <el-form-item label-width="0" prop="password">
          <el-input
            v-model="formData.password"
            placeholder="请输入密码"
            prefix-icon="iconfont icon-password"
            show-password
            :style="{ width: '100%' }"
          ></el-input>
        </el-form-item>

        <el-button
          :loading="loading"
          type="primary"
          style="width: 100%; height: 60px; background-color: transparent"
          @click.native.prevent="submitForm"
          >登录</el-button
        >
      </el-form>
    </el-card>
  </div>
</template>

<script>
export default {
    name: '',
    components: {},
    data(){
        return {
      formData: {
        username: '',
        password: undefined,
      },
       rules: {
        username: [{
          required: true,
          message: '请输入用户名',
          trigger: 'blur'
        }, {
          pattern: /^[a-zA-Z0-9_-]{4,16}$/,
          message: '请输入4-16位用户名',
          trigger: 'blur'
        }],
        password: [{
          required: true,
          message: '请输入密码',
          trigger: 'blur'
        }, {
          pattern: /^(?![0-9]+$)(?![a-zA-Z]+$)[0-9A-Za-z\\W]{6,18}$/,
          message: '密码必须由6-18位字母、数字组成',
          trigger: 'blur'
        }],
      },
      loading: false,
      passwordType: 'password',
      redirect: undefined
    }
    },
    created(){},
    mounted(){},
    computed: {},
    methods: {
       submitForm() {
      this.$refs['elForm'].validate(valid => {
        if (!valid) return
        // TODO 提交表单
        console.log('登录事件执行');
      })
    },
    }
}
</script>

<style lang="less" scoped>
// 字体图标
@import url("//at.alicdn.com/t/font_2761537_p99sgzglu6.css");
// 宽度小于650,宽度改变
@media screen and (max-width: 650px) {
  .box-login {
    width: 100% !important;
    height: 50% !important;
  }
}
#app {
  overflow: hidden;
  width: 100vw;
  height: 100vh;
  .box-login {
    position: absolute;
    top: 40%;
    left: 50%;
    transform: translate(-50%, -50%);
    width: 600px;
    height: 400px;
    background-color: transparent;
    border: 0;
    .el-input {
      display: inline-block;
      height: 50px;
      width: 100%;

      input {
        border: 0px;
        -webkit-appearance: none;
        border-radius: 0px;
        padding: 12px 5px 12px 15px;
        color: #eee;
        height: 100%;
        background-color: transparent !important;
        caret-color: #eee;
        &:-webkit-autofill {
          box-shadow: 0 0 0px 1000px #9ab8d1 inset !important;
          -webkit-text-fill-color: #4a79aa !important;
        }
      }
    }
    /deep/ .el-input--medium .el-input__inner {
      height: 50px;
      line-height: 50px;
      background-color: transparent !important;
    }

    .el-form-item {
      border: 1px solid rgba(255, 255, 255, 0.1);
      background: rgba(0, 0, 0, 0.1);
      border-radius: 5px;
      color: #454545;
    }
    .title-container {
      position: relative;

      .title {
        font-size: 45px;
        color: #055b65;
        margin: 0px auto 50px auto;
        text-align: center;
        font-weight: bold;
      }
    }
  }
}
</style> 
