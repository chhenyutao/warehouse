<template>
  <div>

    <p>标题</p>
    <input type="text" v-model="title" style="width: 98%">
    <p>内容</p>
    <input type="text" v-model="content" style="width: 99%;height: 300px" ><br><br>
    <button type="button" @click="add()">添加</button>
    <button type="button" @click="del()">取消</button>
  </div>
</template>

<script>
  import store from '../store/index.js'
export default {
  name: 'Add',
  store,
  data () {
    return {
      title:'',
      content:''
    }
  },
  methods: {
    add(){
      store.commit('addItem',{
        title: this.title,
        content: this.content
      })
      this.title=''
        this.content=''
      this.$router.push('/home/list')
    },
    del(){
      this.$router.push('/home/user')
    }
  }
}
</script>

<style scoped lang="scss">
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
  button{
    background-color: #66afe9;
    font-size: 24px;
    border-radius: 10px;
    width: 100px;
  }
</style>
