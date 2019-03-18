<template>
    <div class="f" v-show="t==1?true:t==2?data.finished:!data.finished">
        <div class="f1">
            <input type="checkbox" v-model="data.finished"/>
        </div>
        <div :class="['f2',{'edit':isedit}]" @dblclick="dbl">
            <div>{{data.title}}</div>
            <input ref="aa" v-focus v-model="data.title" @keyup.esc="cancelEdit" @keyup.enter="edited" @blur="edited">
        </div>
        <div class="f3"><a href="javascript:;" @click="del">删除</a></div>
    </div>
</template>

<script>
  export default {
    name: "Todo",
    data:function () {
      return {
        data:this.d,
        v:this.t,
        isedit:false,
        beforeValue:'',
      }
    },
    props:['d','t'],
    methods:{
      del:function () {
        if (confirm('您确定要删除吗？')) {
          this.$emit('del')
        }
      },
      dbl:function () {
        this.beforeValue = this.data.title;
        this.isedit = true;
      },
      cancelEdit:function () {
        this.isedit = false;
        this.data.title = this.beforeValue
      },
      edited:function () {
        this.isedit = false;
      }
    },
    directives:{
      "focus":{
        update(el){
          el.focus();
        }
      }
    }
  }
</script>

<style scoped>
    .f{
        display: flex;
    }
    .f1{
        flex: .1;
    }
    .f2{
        flex: .8;
    }
    .f2 input{
        display: none;
    }
    .f2.edit input{
        display: inline;
    }
    .f2.edit div{
        display: none;
    }
    .f3{
        flex: .1;
    }
</style>