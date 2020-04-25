<template>
  <div @click="clickHandle">

    <div class="userinfo" @click="bindViewTap">
      <img class="userinfo-avatar" src="/static/images/user.png" background-size="cover" />


      <!--      <i-card title="微信程序" extra="内容" thumb="https://i.loli.net/2017/08/21/599a521472424.jpg">-->
<!--        <view slot="content">一二三四五</view>-->
<!--        <view slot="footer">上山打老虎</view>-->
<!--      </i-card>-->
    </div>
    <div>
      <i-panel title="基础用法">
        <i-input value="{{ value1 }}" title="收货人：" autofocus placeholder="名字" />
        <i-input value="{{ value2 }}" type="number" title="联系电话：" placeholder="请输入手机号" />
        <i-input value="{{ value3 }}" type="textarea" title="详细地址：" placeholder="请输入详细地址(最多50字)" maxlength="50" />
        <i-input value="{{ value4 }}" title="用户信息" placeholder="请输入详细信息：" />
      </i-panel>
    </div>
    <div class="usermotto">
      <form class="form-container">
        <i-row>
          <i-col span="12" i-class="col-class">
            <i-button type="primary" @click="handleDefault">成功</i-button>
          </i-col>
          <i-col span="12" i-class="col-class">
            <i-button type="default" @click="handleSuccess">失败</i-button>
          </i-col>
        </i-row>
<!--        <i-button type="primary" @click="handleWarning">警告</i-button>-->
<!--        <i-button type="primary" @click="govuex">跳转vuex</i-button>-->
<!--        <i-button type="primary" @click="bindViewTap">日志</i-button>-->
      </form>
    </div>
    <i-tab-bar current="{{ current }}" fixed="true" color="#f759ab" bindchange="handleChange">
      <i-tab-bar-item key="homepage" icon="homepage" current-icon="homepage_fill" title="首页"></i-tab-bar-item>
      <i-tab-bar-item key="group" icon="group" current-icon="group_fill" title="朋友"></i-tab-bar-item>
      <i-tab-bar-item key="remind" icon="remind" current-icon="remind_fill" title="通知"></i-tab-bar-item>
      <i-tab-bar-item key="mine" icon="mine" current-icon="mine_fill" title="我的"></i-tab-bar-item>
    </i-tab-bar>
    <i-message id="message" />
  </div>
</template>

<script>
import card from '@/components/card'
import { $Message } from '../../../static/ivew/base/index'
export default {
  data () {
    return {
      current: 'homepage',
      value1:'',
      value2:'',
      value3:'',
      value4:'',
      motto: 'Hello miniprograme',
      userInfo: {
        nickName: '刘亚威',
        avatarUrl: 'http://mpvue.com/assets/logo.png'
      }
    }
  },

  components: {
    card,
    $Message
  },

  methods: {
    handleChange ({ detail }) {
      this.setData({
        current: detail.key
      });
    },
    handleDefault () {
      $Message({
        content: '这是一条普通提醒'
      });
    },
    handleSuccess () {
      $Message({
        content: '这是一条成功提醒',
        type: 'success'
      });
    },
    handleWarning () {
      $Message({
        content: '这是一条警告提醒',
        type: 'warning'
      });
    },
    handleError () {
      $Message({
        content: '这是一条错误提醒',
        type: 'error'
      });
    },
    handleDuration () {
      $Message({
        content: '我将在 5 秒后消失',
        duration: 5
      });
    },
    govuex(){
      const url = '../counter/main'
      if (mpvuePlatform === 'wx') {
        mpvue.switchTab({ url })
      } else {
        mpvue.navigateTo({ url })
      }
    },
    bindViewTap () {
      const url = '../logs/main'
      if (mpvuePlatform === 'wx') {
        mpvue.switchTab({ url })
      } else {
        mpvue.navigateTo({ url })
      }
    },
    clickHandle (ev) {
      console.log('clickHandle:', ev)
      // throw {message: 'custom test'}
    }
  },

  created () {
    // let app = getApp()
  }
}
</script>

<style scoped>
.userinfo {
  display: flex;
  flex-direction: column;
  align-items: center;
}

.userinfo-avatar {
  width: 128rpx;
  height: 128rpx;
  margin: 20rpx;
  border-radius: 50%;
}

.userinfo-nickname {
  color: #aaa;
}

.usermotto {
  margin-top: 30px;
}

.form-control {
  display: block;
  padding: 0 12px;
  margin-bottom: 5px;
  border: 1px solid #ccc;
}
.all{
  width:7.5rem;
  height:1rem;
  background-color:blue;
}
.all:after{
  display:block;
  content:'';
  clear:both;
}
.left{
  float:left;
  width:3rem;
  height:1rem;
  background-color:red;
}

.right{
  float:left;
  width:4.5rem;
  height:1rem;
  background-color:green;
}
</style>
