<template>
  <div>
    <group title="登录">
      <x-input title="用户名" name="username" v-model="userName" placeholder="请输入用户名" ></x-input>
      <x-input title="年龄" name="age" v-model="age" placeholder="请输入年龄"></x-input>
    </group>
    <a v-on:click="addUser">登录</a>
  </div>
</template>

<script>
import axios from 'axios';
import { Group, XButton, XInput } from 'vux';

export default {
  components: {
    Group,
    XButton,
    XInput
  },
  data () {
    return {
      userName: 'tessdft',
      age: 10
    }
  },
  methods: {
    addUser () {
      let userName = this.userName;
      let age = this.age;
      debugger;
      axios.post('/api/user/addUser', {
        username: userName,
        age: age
      }).then((res) => {
        console.log(res);
      }).then((res) => {
        console.log(res);
      });
    }
  }
}
</script>

<style scoped>
.login-btn {
  display: block;
  width: 80%;
  margin: 2rem 10% 0 10%;
  border-radius: 22px;
}
</style>
