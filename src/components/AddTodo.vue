<template>
    <div>
        <h3>添加小目标</h3>
        <input v-model="todo" type="text" placeholder="输入小目标后，按回车确认" @keyup.enter="add"/>
    </div>
</template>

<script>
  export default {
    name: "AddTodo",
    data:function(){
      return {
        todo:'',
      }
    },
    methods:{
      add:function () {
        if(!this.todo){
          alert('请填写小目标')
        }else {
          this.$emit('todo',this.todo);//向外发送
          this.todo = '';
        }
      }
    }
  }
</script>

<style scoped>
    input{
        width: 100%;
        height: 50px;
        line-height: 50px;
    }
</style>