<template>
  <div>
    <img alt="Vue logo" src="../assets/logo.png"><br>
    <h1>欢迎来到后台管理系统</h1>
    <form  v-if="!isReg">
    账号：
    <input type="text" v-model="name"><br><br>
    密码：
    <input type="password" v-model="password"><br><br>
    <button type="button" @click="login()">登录</button>&nbsp;&nbsp;
    <button type="button" @click="reg()">注册</button>

    </form>
    <form  v-else>
      账号：
      <input type="text" v-model="name"><br><br>
      密码：
      <input type="password" v-model="password"><br><br>
      再次输入密码：
      <input type="password" v-model="repeat" style="margin-right: 62px"><br><br>
      <button type="button" @click="addUser()">确定</button>&nbsp;&nbsp;
      <button type="button" @click="cancel()">取消</button>
    </form>
  </div>
</template>

<script>
export default {
  name: 'Login',
  data(){
    return{
      isReg:false,
      name:'',
      password:'',
      repeat:''
    }
  },
  methods: {
    login(){
      if (localStorage.getItem("name")===this.name && localStorage.getItem("password") === this.password){
        this.name=''
        this.password=''
        this.$router.push('/home/list')
      }else {
        alert('用户名密码不正确！')
      }

    },
    reg(){
      this.isReg =true
    },
    cancel(){
      this.isReg=false
    },
    addUser(){
      if(this.password===this.repeat){
        localStorage.setItem("name",this.name)
        localStorage.setItem("password",this.password)
        this.name=''
        this.password=''
        this.isReg=false
      }else {
       alert('两次输入的密码不一致！')
      }
    }
  }
}
</script>

<style scoped lang="scss">
  div{
    text-align: center;
  }
  button{
    background-color: #66afe9;
    font-size: 24px;
    border-radius: 10px;
    width: 100px;
  }
  input{
    border: 1px solid #ccc;
    padding: 7px 0px;
    border-radius: 3px;
    padding-left:5px;
    -webkit-box-shadow: inset 0 1px 1px rgba(0,0,0,.075);
    box-shadow: inset 0 1px 1px rgba(0,0,0,.075);
    -webkit-transition: border-color ease-in-out .15s,-webkit-box-shadow ease-in-out .15s;
    -o-transition: border-color ease-in-out .15s,box-shadow ease-in-out .15s;
    transition: border-color ease-in-out .15s,box-shadow ease-in-out .15s
  }
  input:focus{
    border-color: #66afe9;
    outline: 0;
    -webkit-box-shadow: inset 0 1px 1px rgba(0,0,0,.075),0 0 8px rgba(102,175,233,.6);
    box-shadow: inset 0 1px 1px rgba(0,0,0,.075),0 0 8px rgba(102,175,233,.6)
  }
</style>
