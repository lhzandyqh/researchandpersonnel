<template>
  <div class="login-container">
    <div class="head">
      <div class="logo">
        <img src="../../assets/icon/keyan.png">
        <span> 科研管理智能平台</span>
      </div>
      <div class="user" @click="dialogVisible = true">
        <img src="../../assets/icon/denglu.png">
        登录
      </div>
    </div>
    <div class="card w clearfix" style="margin-top: 60px">
      <div class="card_container ">
        <div class="box-hd">
          <h3>校园风采</h3>
          <a href="#">查看更多</a>
        </div>
        <div class="card_body">
          <div class="kapian">
            <el-carousel height="300px">
              <el-carousel-item v-for="(item, index) in schna" :key="index">
                <img :src="item" alt="">
              </el-carousel-item>
            </el-carousel>
          </div>
        </div>
      </div>
      <div class="card_container ">
        <div class="box-hd">
          <h3>新闻通知</h3>
          <a href="#">查看更多</a>
        </div>
        <div class="card_body">
          <div class="kapian">
            <ul>
              <li>
                <img src="../../assets/img/tupian4.jpg">
                <div class="left">
                  <span>财政部关于印发《中央财政科研项目专家咨询费管理办法》的通知</span>
                </div>
                <div class="right">
                  <div class="first_line">
                    <!--                    <img class="img" src="../../assets/icon/dianzan.png">-->
                  </div>
                  <div class="second_line">
                    <span>评论：32</span>
                  </div>
                </div>
              </li>
              <li>
                <img src="../../assets/img/tupian5.jpg">
                <div class="left">
                  <span>过好“紧日子” 花好每笔钱——聚焦2020年中央部门“晒预算”</span>
                </div>
                <div class="right">
                  <div class="first_line">
                    <!--                    <img class="img" src="../../assets/icon/dianzan.png">-->
                  </div>
                  <div class="second_line">
                    <span>评论：22</span>
                  </div>
                </div>
              </li>
              <li class="noline">
                <img src="../../assets/img/tupian6.jpg">
                <div class="left">
                  <span>科技日报：整治形式主义始终在路上</span>
                </div>
                <div class="right">
                  <div class="first_line">
                    <!--                    <img class="img" src="../../assets/icon/dianzan.png">-->
                  </div>
                  <div class="second_line">
                    <span>评论：15</span>
                  </div>
                </div>
              </li>
            </ul>
          </div>
        </div>
      </div>
    </div>
    <div class="card w clearfix">
      <div class="card_container ">
        <div class="box-hd">
          <h3>科研动态</h3>
          <a href="#">查看更多</a>
        </div>
        <div class="card_body">
          <div class="kapian">
            <ul>
              <li>
                <img src="../../assets/img/tupian7.jpg">
                <div class="left">
                  <span>关于转发2019年度河北省社会科学基金项目申报工作的通知</span>
                </div>
                <div class="right">
                  <div class="first_line">
                    <!--                    <img class="img" src="../../assets/icon/dianzan.png">-->
                  </div>
                  <div class="second_line">
                    <span>评论：42</span>
                  </div>
                </div>
              </li>
              <li>
                <img src="../../assets/img/tupian8.jpg">
                <div class="left">
                  <span>电子学院王贺/刘子艺团队在新型电子器件方面取得最新成果</span>
                </div>
                <div class="right">
                  <div class="first_line">
                    <!--                    <img class="img" src="../../assets/icon/dianzan.png">-->
                  </div>
                  <div class="second_line">
                    <span>评论：22</span>
                  </div>
                </div>
              </li>
              <li class="noline">
                <img src="../../assets/img/tupian9.jpg">
                <div class="left">
                  <span>苏秀宁教授发表关于未来图书馆的新思考</span>
                </div>
                <div class="right">
                  <div class="first_line">
                    <!--                    <img class="img" src="../../assets/icon/dianzan.png">-->
                  </div>
                  <div class="second_line">
                    <span>评论：18</span>
                  </div>
                </div>
              </li>
            </ul>
          </div>
        </div>
      </div>
      <div class="card_container ">
        <div class="box-hd">
          <h3>成果展示</h3>
          <a href="#">查看全部</a>
        </div>
        <div class="card_body">
          <div class="kapian">
            <ul>
              <li>
                <img src="../../assets/img/tupian10.jpg">
                <div class="left">
                  <span>刘年教授荣获中国产学研合作创新奖</span>
                </div>
                <div class="right">
                  <div class="first_line">
                    <!--                    <img class="img" src="../../assets/icon/dianzan.png">-->
                  </div>
                  <div class="second_line">
                    <span>评论：16</span>
                  </div>
                </div>
              </li>
              <li>
                <img src="../../assets/img/tupian11.jpg">
                <div class="left">
                  <span>河北省第三届教育科学优秀成果奖情况一览表</span>
                </div>
                <div class="right">
                  <div class="first_line">
                    <!--                    <img class="img" src="../../assets/icon/dianzan.png">-->
                  </div>
                  <div class="second_line">
                    <span>评论：12</span>
                  </div>
                </div>
              </li>
              <li class="noline">
                <img src="../../assets/img/tupian12.jpg">
                <div class="left">
                  <span>王可玲教授关于高职学生低谷期心理研究论文</span>
                </div>
                <div class="right">
                  <div class="first_line">
                    <!--                    <img class="img" src="../../assets/icon/dianzan.png">-->
                  </div>
                  <div class="second_line">
                    <span>评论：27</span>
                  </div>
                </div>
              </li>
            </ul>
          </div>
        </div>
      </div>
    </div>
    <div class="card w clearfix">
      <div class="card_container_two">
        <div class="box-hd">
          <h3>常用工具</h3>
        </div>
        <div class="card_body">
          <div class="kapian_two">
            <div class="kapian_item">
              <div style="text-align: center;margin-top: 5px">
                <img style="width: 65px;height: 65px" src="../../assets/icon/mulu.png">
              </div>
              <div style="text-align: center;margin-top: 5px">
                <span style="font-size: 12px;color: white">期刊目录查询</span>
              </div>
            </div>
            <div class="kapian_item">
              <div style="text-align: center;margin-top: 5px">
                <img style="width: 70px;height: 70px" src="../../assets/icon/jiangli.png">
              </div>
              <div style="text-align: center">
                <span style="font-size: 12px;color: white">奖励信息查询</span>
              </div>
            </div>
            <div class="kapian_item">
              <div style="text-align: center;margin-top: 5px">
                <img style="width: 70px;height: 70px" src="../../assets/icon/xiangmu.png">
              </div>
              <div style="text-align: center">
                <span style="font-size: 12px;color: white">项目信息查询</span>
              </div>
            </div>
            <div class="kapian_item">
              <div style="text-align: center;margin-top: 5px">
                <img style="width: 65px;height: 65px" src="../../assets/icon/tushuguan.png">
              </div>
              <div style="text-align: center">
                <span style="font-size: 12px;color: white">图书馆</span>
              </div>
            </div>
            <div class="kapian_item">
              <div style="text-align: center;margin-top: 5px">
                <img style="width: 65px;height: 65px" src="../../assets/icon/zhiwang.png">
              </div>
              <div style="text-align: center">
                <span style="font-size: 12px;color: white">中国知网</span>
              </div>
            </div>
          </div>
        </div>
      </div>
    </div>
    <div class="footer">
      <div class="w">
        <div class="foot_img">
          <img src="../../assets/logo.png">
        </div>
        <div class="copyright">
          <p>
            ©2020年ZKRT Inc.保留所有权利。</p>
          <!--          <a href="#" class="app" @click="gotoAboutUs">关于我们</a>-->
        </div>
        <div class="links">
          <dl>
            <dt>关于中科瑞通</dt>
            <dd><a href="#">联系方式</a></dd>
            <dd><a href="#">团队成员</a></dd>
            <dd><a href="#">项目展示</a></dd>
            <dd><a href="#">客户服务</a></dd>
            <dd><a href="#">帮助</a></dd>
          </dl>
        </div>
      </div>
    </div>

    <el-dialog
      title="请登录"
      :visible.sync="dialogVisible"
      width="30%"
      :before-close="handleClose"
    >
      <!--      <span>这是一段信息</span>-->
      <!--      <span slot="footer" class="dialog-footer">-->
      <!--        <el-button @click="dialogVisible = false">取 消</el-button>-->
      <!--        <el-button type="primary" @click="dialogVisible = false">确 定</el-button>-->
      <!--      </span>-->
      <el-form ref="loginForm" :model="loginForm" :rules="loginRules" class="login-form" auto-complete="on" label-position="left">
        <!--        <div class="title-container">-->
        <!--          <h3 class="title">-->
        <!--            {{ $t('login.title') }}-->
        <!--          </h3>-->
        <!--          <lang-select class="set-language" />-->
        <!--        </div>-->

        <el-form-item prop="username">
          <span class="svg-container">
            <svg-icon icon-class="user" />
          </span>
          <el-input
            ref="username"
            v-model="loginForm.username"
            :placeholder="$t('login.username')"
            name="username"
            type="text"
            auto-complete="on"
          />
        </el-form-item>

        <el-form-item prop="password" style="margin-top: 10px">
          <span class="svg-container">
            <svg-icon icon-class="password" />
          </span>
          <el-input
            ref="password"
            v-model="loginForm.password"
            :type="passwordType"
            :placeholder="$t('login.password')"
            name="password"
            auto-complete="on"
            @keyup.enter.native="handleLogin"
          />
          <span class="show-pwd" @click="showPwd">
            <svg-icon :icon-class="passwordType === 'password' ? 'eye' : 'eye-open'" />
          </span>
        </el-form-item>

        <el-button :loading="loading" type="primary" style="width:100%;margin-bottom:30px;;margin-top: 20px;height: 40px" @click.native.prevent="handleLogin">
          {{ $t('login.logIn') }}
        </el-button>

        <div style="position:relative">
          <div class="tips">
            <span>{{ $t('login.username') }} : admin</span>
            <span>{{ $t('login.password') }} : {{ $t('login.any') }}</span>
          </div>
          <div class="tips">
            <span style="margin-right:18px;">
              {{ $t('login.username') }} : editor
            </span>
            <span>{{ $t('login.password') }} : {{ $t('login.any') }}</span>
          </div>

          <el-button class="thirdparty-button" type="primary" @click="showDialog=true">
            {{ $t('login.thirdparty') }}
          </el-button>
        </div>
      </el-form>
    </el-dialog>
    <!--    <el-form ref="loginForm" :model="loginForm" :rules="loginRules" class="login-form" auto-complete="on" label-position="left">-->
    <!--      <div class="title-container">-->
    <!--        <h3 class="title">-->
    <!--          {{ $t('login.title') }}-->
    <!--        </h3>-->
    <!--        <lang-select class="set-language" />-->
    <!--      </div>-->

    <!--      <el-form-item prop="username">-->
    <!--        <span class="svg-container">-->
    <!--          <svg-icon icon-class="user" />-->
    <!--        </span>-->
    <!--        <el-input-->
    <!--          ref="username"-->
    <!--          v-model="loginForm.username"-->
    <!--          :placeholder="$t('login.username')"-->
    <!--          name="username"-->
    <!--          type="text"-->
    <!--          auto-complete="on"-->
    <!--        />-->
    <!--      </el-form-item>-->

    <!--      <el-form-item prop="password">-->
    <!--        <span class="svg-container">-->
    <!--          <svg-icon icon-class="password" />-->
    <!--        </span>-->
    <!--        <el-input-->
    <!--          ref="password"-->
    <!--          v-model="loginForm.password"-->
    <!--          :type="passwordType"-->
    <!--          :placeholder="$t('login.password')"-->
    <!--          name="password"-->
    <!--          auto-complete="on"-->
    <!--          @keyup.enter.native="handleLogin"-->
    <!--        />-->
    <!--        <span class="show-pwd" @click="showPwd">-->
    <!--          <svg-icon :icon-class="passwordType === 'password' ? 'eye' : 'eye-open'" />-->
    <!--        </span>-->
    <!--      </el-form-item>-->

    <!--      <el-button :loading="loading" type="primary" style="width:100%;margin-bottom:30px;" @click.native.prevent="handleLogin">-->
    <!--        {{ $t('login.logIn') }}-->
    <!--      </el-button>-->

    <!--      <div style="position:relative">-->
    <!--        <div class="tips">-->
    <!--          <span>{{ $t('login.username') }} : admin</span>-->
    <!--          <span>{{ $t('login.password') }} : {{ $t('login.any') }}</span>-->
    <!--        </div>-->
    <!--        <div class="tips">-->
    <!--          <span style="margin-right:18px;">-->
    <!--            {{ $t('login.username') }} : editor-->
    <!--          </span>-->
    <!--          <span>{{ $t('login.password') }} : {{ $t('login.any') }}</span>-->
    <!--        </div>-->

    <!--        <el-button class="thirdparty-button" type="primary" @click="showDialog=true">-->
    <!--          {{ $t('login.thirdparty') }}-->
    <!--        </el-button>-->
    <!--      </div>-->
    <!--    </el-form>-->

    <!--    <el-dialog :title="$t('login.thirdparty')" :visible.sync="showDialog">-->
    <!--      {{ $t('login.thirdpartyTips') }}-->
    <!--      <br>-->
    <!--      <br>-->
    <!--      <br>-->
    <!--      <social-sign />-->
    <!--    </el-dialog>-->
  </div>
</template>

<script>
import { validUsername } from '@/utils/validate'
// import LangSelect from '@/components/LangSelect'
// import SocialSign from './socialsignin'

export default {
  name: 'Login',
  // components: { LangSelect, SocialSign },
  data() {
    const validateUsername = (rule, value, callback) => {
      if (!validUsername(value)) {
        callback(new Error('Please enter the correct user name'))
      } else {
        callback()
      }
    }
    const validatePassword = (rule, value, callback) => {
      if (value.length < 6) {
        callback(new Error('The password can not be less than 6 digits'))
      } else {
        callback()
      }
    }
    return {
      schna: ['http://zhihejiaoyu.cn/reveal/img/keyan1.jpg', 'http://zhihejiaoyu.cn/reveal/img/keyan2.jpg'],
      dialogVisible: false,
      loginForm: {
        username: 'admin',
        password: '111111'
      },
      loginRules: {
        username: [{ required: true, trigger: 'blur', validator: validateUsername }],
        password: [{ required: true, trigger: 'blur', validator: validatePassword }]
      },
      passwordType: 'password',
      loading: false,
      showDialog: false,
      redirect: undefined
    }
  },
  watch: {
    $route: {
      handler: function(route) {
        this.redirect = route.query && route.query.redirect
      },
      immediate: true
    }
  },
  created() {
    // window.addEventListener('hashchange', this.afterQRScan)
  },
  mounted() {
    if (this.loginForm.username === '') {
      this.$refs.username.focus()
    } else if (this.loginForm.password === '') {
      this.$refs.password.focus()
    }
  },
  destroyed() {
    // window.removeEventListener('hashchange', this.afterQRScan)
  },
  methods: {
    showPwd() {
      if (this.passwordType === 'password') {
        this.passwordType = ''
      } else {
        this.passwordType = 'password'
      }
      this.$nextTick(() => {
        this.$refs.password.focus()
      })
    },
    handleLogin() {
      this.$refs.loginForm.validate(valid => {
        if (valid) {
          this.loading = true
          this.$store.dispatch('LoginByUsername', this.loginForm).then(() => {
            this.loading = false
            this.$router.push({ path: this.redirect || '/' })
          }).catch(() => {
            this.loading = false
          })
        } else {
          console.log('error submit!!')
          return false
        }
      })
    },
    afterQRScan() {
      // const hash = window.location.hash.slice(1)
      // const hashObj = getQueryObject(hash)
      // const originUrl = window.location.origin
      // history.replaceState({}, '', originUrl)
      // const codeMap = {
      //   wechat: 'code',
      //   tencent: 'code'
      // }
      // const codeName = hashObj[codeMap[this.auth_type]]
      // if (!codeName) {
      //   alert('第三方登录失败')
      // } else {
      //   this.$store.dispatch('LoginByThirdparty', codeName).then(() => {
      //     this.$router.push({ path: '/' })
      //   })
      // }
    }
  }
}
</script>

<style rel="stylesheet/scss" lang="scss">
  /* 修复input 背景不协调 和光标变色 */
  /* Detail see https://github.com/PanJiaChen/vue-element-admin/pull/927 */

  $bg:#283443;
  $light_gray: #141519;
  $cursor: #141519;

  @supports (-webkit-mask: none) and (not (cater-color: $cursor)) {
    .login-container .el-input input{
      color: $cursor;
      &::first-line {
        color: $light_gray;
      }
    }
  }

  /* reset element-ui css */
  .login-container {
    .el-input {
      display: inline-block;
      height: 47px;
      width: 85%;
      input {
        background: transparent;
        border: 0px;
        -webkit-appearance: none;
        border-radius: 0px;
        padding: 12px 5px 12px 15px;
        color: $light_gray;
        height: 47px;
        caret-color: $cursor;
      }
    }
    .el-form-item {
      border: 1px solid rgba(255, 255, 255, 0.1);
      background: rgba(0, 0, 0, 0.1);
      border-radius: 5px;
      color: #454545;
    }
  }
</style>

<style rel="stylesheet/scss" lang="scss" scoped>
$bg: #f0f0f0;
$dark_gray:#889aa4;
$light_gray:#eee;

.login-container {
  min-height: 100%;
  width: 100%;
  background-color: $bg;
  overflow: hidden;
  .login-form {
    position: relative;
    width: 520px;
    max-width: 100%;
    padding: 0px 35px 0;
    margin: 0 auto;
    overflow: hidden;
  }
  .tips {
    font-size: 14px;
    color: #fff;
    margin-bottom: 10px;
    span {
      &:first-of-type {
        margin-right: 16px;
      }
    }
  }
  .svg-container {
    padding: 6px 5px 6px 15px;
    color: $dark_gray;
    vertical-align: middle;
    width: 30px;
    display: inline-block;
  }
  .title-container {
    position: center;
    .title {
      font-size: 26px;
      color: $light_gray;
      margin: 0px auto 40px auto;
      text-align: center;
      font-weight: bold;
    }
    .set-language {
      color: #fff;
      position: absolute;
      top: 3px;
      font-size:18px;
      right: 0px;
      cursor: pointer;
    }
  }
  .show-pwd {
    position: absolute;
    right: 10px;
    top: 7px;
    font-size: 16px;
    color: $dark_gray;
    cursor: pointer;
    user-select: none;
  }
  .thirdparty-button {
    position: absolute;
    right: 0;
    bottom: 6px;
  }
}

* {
  margin: 0;
  padding: 0;
}
li {
  list-style: none;
}
a {
  text-decoration: none;
}
.clearfix:before,.clearfix:after {
  content: '';
  display: table;
}
.clearfix:after {
  clear: both;
}
.clearfix {
  *zoom: 1;
}
body {
  background-color: #f3f5f7;
  /* height: 3000px; */
}
.w {
  width: 1200px;
  margin: 0 auto;
}
.head {
  height: 80px;
  background-color: #f3f5f7;
  /*margin: 30px auto;*/
  /*margin: 30px auto;*/
}
.logo {
  float: left;
  margin-left: 30px;
  width: 400px;
  height: 80px;
  /*background-color: purple;*/
}
.logo img {
  float: left;
  display: block;
  width: 80px;
  height: 80px;
}
.logo span {
  float: left;
  display: block;
  width: 200px;
  height: 80px;
  font-size: 20px;
  font-weight: bold;
  line-height: 80px;
  margin-left: 10px;
}
.nav {
  float: left;
  margin-left: 60px;
}
.nav ul li {
  float: left;
  margin: 0 15px;
}
.nav ul li a {
  display: block;
  height: 42px;
  padding: 0 10px;
  line-height: 42px;
  font-size: 18px;
  color: #050505;
}
.nav ul li a:hover {
  border-bottom:2px solid #ff1c23;
}

.search {
  float: left;
  width: 412px;
  height: 42px;
  background-color: deepskyblue;
  margin-left: 70px;
}

.search input {
  float: left;
  width: 345px;
  height: 40px;
  border: 1px solid #00a4ff;
  border-right: 0;
  color: #bfbfbf;
  font-size: 14px;
  padding-left: 15px;
}
.search button {
  float: left;
  width: 50px;
  height: 42px;
  background-color: #00a4ff;
  border: 0;
}
.user {
  padding-top: 20px;
  float: right;
  line-height: 42px;
  margin-right: 30px;
  font-size: 14px;
  font-weight: bold;
  cursor: pointer;
  color: #818181;
}
.user img {
  vertical-align: middle;
  width: 20px;
  height: 20px;
  /*cursor: pointer;*/
  /*background-color: #bfbfbf;*/
}
.banner {
  height: 600px;
  background-color: white;
}
.banner .w {
  height: 600px;
  background-color: pink;
}
.subnav {
  float: left;
  width: 190px;
  height: 421px;
  background: rgba(0,0,0, 0.3);
}
.subnav ul li {
  height: 45px;
  line-height: 45px;
  padding: 0 20px;
}
.subnav ul li a {
  font-size: 14px;
  color: #fff;
}
.subnav ul li a span {
  float: right;
}
.subnav ul li a:hover {
  color:#00a4ff
}
.course {
  float: right;
  width: 230px;
  height: 300px;
  margin-top: 50px;
  background-color: white;
}
.course h2 {
  height: 48px;
  background-color: #9bceea;
  text-align: center;
  line-height: 48px;
  font-size: 18px;
  color: white;
}
.bd {
  padding: 0 20px;
}
.bd ul li {
  padding: 14px 0;
  border-bottom: 1px solid #ccc;
}
.bd ul li h4 {
  font-size: 16px;
  color: #4e4e4e;
}
.bd ul li p {
  font-size: 12px;
  color: #a5a5a5;
}
.bd .more {
  display: block;
  height: 38px;
  border: 1px solid #00a4ff;
  margin-top: 5px;
  text-align: center;
  line-height: 38px;
  color: #00a4ff;
  font-size: 16px;
  font-weight: 700;
}
.goods {
  height: 60px;
  background-color: #fff;
  margin-top: 10px;
  box-shadow: 0 2px 3px 3px rgba(0, 0, 0, 0.1);
  line-height: 60px;
}
.goods h3 {
  float: left;
  margin-left: 30px;
  font-size: 16px;
  color: #00a4ff;
}
.goods ul {
  float: left;
  margin-left: 30px;
}
.goods ul li {
  float: left;
}
.goods ul li a {
  padding: 0 30px;
  font-size: 16px;
  color: #050505;
  border-left: 1px solid #ccc;
}
.mod {
  float: right;
  margin-right: 30px;
  font-size: 14px;
  color: #00a4ff;
}
.box {
  margin-top: 30px;
}
.box-hd {
  height: 45px;
}
.box-hd h3 {
  float: left;
  font-size: 20px;
  color: #494949;
}
.box-hd a {
  float: right;
  font-size: 12px;
  color: #a5a5a5;
  line-height: 45px;
  margin-right: 30px;
}
.box-bd ul li .hot {
  width: 30px;
  height: 15px;
  background-color:#00a4ff;
}
.box-bd ul li em {
  position: absolute;
  top:4px;
  right: -4px;
}
.box-bd ul {
  width: 1225px;
}
.box-bd ul li {
  position: relative;
  float: left;
  width: 228px;
  height: 270px;
  background-color: white;
  margin-right: 15px;
  margin-bottom: 15px;
}
.box-bd ul li img {
  width: 100%;
  height: 155px;
  background-color: plum;
}
.box-bd ul li h4 {
  margin: 20px 20px 20px 25px;
  font-size: 14px;
  color: #050505;
  font-weight: 400;
}
.box-bd .info {
  margin: 0 20px 0 25px;
  font-size: 12px;
  color: #999;
}
.box-bd .info span {
  color: #ff7c2d;
}
.footer {
  height: 180px;
  background-color: #fff;
}
.footer .w {
  padding-top: 35px;
}
.copyright {
  float: left;
  margin-left: 30px;
}
.links {
  float: right;
}
.foot_img {
  float: left;
}
.foot_img img {
  width: 100px;
  height: 100px;
  /*background-color: purple;*/
}
.copyright p{
  font-size: 12px;
  color: #666;
  margin: 20px 0 15px 0;
}
.copyright a{
  display: block;
  width: 118px;
  height: 33px;
  border:1px solid #00a4ff;
  text-align: center;
  line-height: 33px;
  color: #00a4ff;
  font-size: 16px;
}
.links dl {
  float: left;
  margin-left: 100px;
}
.links dl dt {
  font-size: 16px;
  color: #333;
  margin-bottom: 5px;
}
.links dl dd a {
  font-size: 12px;
  color: #333;
}
.card {
  margin-top: 30px;
}
.box-card {
  width: 95%;
  height: 180px;
  padding: 0;
}
.box-card ul {
  width: 100%;
  height: 180px;
  background-color: #00a4ff;
}
.card_container {
  width: 600px;
  /*background-color: pink;*/
  float: left;
}
.card_body{
  padding: 10px;
}
.kapian {
  width: 580px;
  height: 300px;
  background-color: white;
  border-radius: 10px;
}
.kapian_two {
  width: 100%;
  height: 150px;
  background-color: white;
  border-radius: 10px;
  padding: 25px;
}
.kapian_item{
  cursor: pointer;
  border-radius: 10px;
  margin-left: 20px;
  float: left;
  background-color: #76ccd2;
  width: 100px;
  height: 100px;
}
.kapian ul {
  width: 580px;
  height: 300px;
}
.kapian ul li {
  height: 100px;
  width: 570px;
  border-bottom-color: #dcdcdc;
  border-bottom-style: solid;
  border-bottom-width: 1px;
  padding-left: 10px;
}
.kapian .noline {
  border-bottom-style: none;
}
.kapian ul li img {
  float: left;
  margin-top: 10px;
  height: 80px;
  width: 200px;
  background-color: #999999;
}
.left {
  float: left;
  width: 300px;
  height: 100px;
  white-space: nowrap;
  overflow: hidden;
  text-overflow: ellipsis;
  /*background-color: pink;*/
}
.left span {
  padding-left: 10px;
  line-height: 100px;
  font-size: 15px;
  cursor: pointer;
}
.right {
  float: left;
}
.first_line {
  height: 50px;
  padding-left: 20px;
}
.first_line .img {
  width: 20px;
  height: 20px;
  background-color: transparent;
  cursor: pointer;
}
.second_line {
  height: 50px;
}
.second_line span {
  font-size: 12px;
  color: #8c8c8c;
  line-height: 50px;
}
.charts{
  padding-top: 20px;
}
  .card_container_two{
    width: 100%;
  }
</style>
