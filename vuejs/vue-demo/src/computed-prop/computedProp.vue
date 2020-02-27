<template>
  <div>
    <div>{{getMsg}}</div>
    <div>{{msg}}</div>
    <div>{{nowDate}}</div>
    <div>{{getNowDate()}}</div>
    <button @click="reverseMsg">点击反转</button>
    <p>1、计算属性是基于它们的响应式依赖进行缓存的：getmsg依赖msg，msg不变，getmsg也不会变化</p>
    <template v-if="loginType === 'username'">
      <label>Username</label>
      <input placeholder="Enter your username" v-model="loginName">
    </template>
    <template v-else>
      <label>Email</label>
      <input placeholder="Enter your email address" v-model="loginName" v-bind:style="{'width': '400px'}" class="mail-input">
    </template>
    <div>{{loginName}}</div>
    <button @click="changeLoginType">改变登录方式</button>
    <input v-model.number="age" type="number">
  </div>
</template>

<script>
  export default {
    name: "computedProp",
    data() {
      return {
        msg: "我是一条消息!",
        loginType:"username",
        loginName: "fafdafa"
      }
    },
    methods:{
      reverseMsg: function () {
        this.msg = this.msg.split("").reverse().join("");
      },
      getNowDate: function () {
        return Date.now();
      },
      changeLoginType: function () {
        if (this.loginType !== 'username') {
          this.loginType = 'username';
        } else {
          this.loginType = "";
        }
      }
    },
    computed: {
      getMsg: function () {
        return this.msg + 'kuaifuping';
      },
      nowDate: function () {
        return Date.now();
      }
    }
  }
</script>

<style scoped>

</style>
