<template>
  <div>
    <img alt="Vue logo" src="../assets/logo.png"><br>
    <p>admin</p>
    <p>欢迎来到个人中心</p>
    <button type="button" @click="insert">添加</button>
  </div>
</template>

<script>
export default {
  methods: {
    insert(){
      this.$router.push('/add')
    }
  }
}
</script>

<style scoped lang="scss">
img{
  display: block;
  margin: auto;
}
  div{
    text-align: center;
  }
  p{
    font-size: 20px;
  }
  button{
    background-color: #66afe9;
    font-size: 20px;
    border-radius: 8px;
    width: 100px;
  }
</style>
