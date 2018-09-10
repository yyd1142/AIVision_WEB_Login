<template>
  <div class="page-wrap" id="page">
    <div class="header-wrap">
      <MyHeader :languageDatas="languageDatas" :language="language"></MyHeader>
    </div>
    <div class="content-wrap">
      <div class="login-wrap my-box-shadow">
        <div class="name">{{languageDatas.name[language]}}</div>
        <el-form :model="ruleForm" :rules="rules" ref="ruleForm">
          <el-form-item prop="name">
            <el-input :placeholder="languageDatas.userNameInput[language]" prefix-icon="iconfont icon-user"
                      v-model="ruleForm.name"></el-input>
          </el-form-item>
          <el-form-item prop="password">
            <el-input :placeholder="languageDatas.passwordInput[language]" prefix-icon="iconfont icon-jiesuo"
                      type="password" v-model="ruleForm.password"></el-input>
          </el-form-item>
          <el-form-item>
            <el-checkbox v-model="ruleForm.rememberPwd">{{languageDatas.rememberPwd[language]}}</el-checkbox>
          </el-form-item>
          <el-form-item>
            <el-button style="width: 100%;" type="primary" @click="submitForm('ruleForm')">
              {{languageDatas.Login[language]}}
            </el-button>
          </el-form-item>
        </el-form>
        <dvi class="forgot-password-wrap">
          <span>{{languageDatas.ForgotPwd[language]}} ?</span>
        </dvi>
      </div>
    </div>
    <!--<div class="footer-wrap">-->
    <!--<MyFooter :languageDatas="languageDatas" :language="language"></MyFooter>-->
    <!--</div>-->
  </div>
</template>

<script>
  import {MyHeader, MyFooter} from '@components';

  export default {
    components: {
      MyHeader, MyFooter
    },
    computed: {
      languageDatas() {
        return this.$store.getters.languageDatas;
      },
    },
    async asyncData(ctx) {
      const language = ctx.query.language || 'en';
      return {
        language: language,
        ruleForm: {
          name: '',
          password: '',
          rememberPwd: false
        },
        rules: {
          name: [
            {message: '请输入账号', trigger: 'blur'},
          ],
          password: [
            {message: '请输入密码', trigger: 'blur'},
          ]
        }
      };
    },
    mounted() {

    },
    methods: {
      submitForm(formName) {
        this.$refs[formName].validate((valid) => {
          if (valid) {
            alert('submit!');
          } else {
            console.log('error submit!!');
            return false;
          }
        });
      },
      resetForm(formName) {
        this.$refs[formName].resetFields();
      }
    }
  }
</script>

<style lang="less">
  .page-wrap {
    width: 100%;
    display: flex;
    display: -webkit-flex;
    height: 100vh;
    flex-direction: column;
    .my-box-shadow {
      -moz-box-shadow: 0px 1px 5px #ccc; /* 老的 Firefox */
      box-shadow: 0px 1px 5px #ccc;
    }
    .header-wrap {
      width: 100%;
      background-color: #fafafa;
      display: flex;
      display: -webkit-flex;
    }
    .content-wrap {
      width: 100%;
      display: flex;
      display: -webkit-flex;
      background-color: #fafafa;
      position: relative;
      flex: 1;

      .login-wrap {
        width: 400px;
        height: 290px;
        bottom: 0;
        top: 0;
        right: 0;
        left: 0;
        margin: auto;
        position: absolute;
        display: flex;
        display: -webkit-flex;
        background-color: #fff;
        border-radius: 4px;
        .name {
          position: absolute;
          width: 100%;
          text-align: center;
          color: #333333;
          font-size: 32px;
          top: -140px;
        }
        .el-form {
          width: 100%;
          padding: 15px;
        }
        .forgot-password-wrap {
          position: absolute;
          bottom: 15px;
          right: 15px;
          color: #606266;
          text-align: right;
          font-size: 14px;
          &:hover {
            text-decoration: underline;
            cursor: pointer;
          }
        }
      }
    }
    .footer-wrap {
      width: 100%;
      background-color: #fff;
      display: flex;
      display: -webkit-flex;
    }
  }
</style>
