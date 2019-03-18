<template>
  <div id="app">
      <Title />
      <AddTodo @todo="addTodo"/>
      <TextInfo :d="data"/>
      <Tab :d="v" @change1="c"/>
      <List :d="data" :t="v" @del="delTodo"/>
  </div>
</template>

<style>
    #app{
        width: 1000px;
        margin: auto;
    }
</style>
<script>
    import Title from "./components/Title";
    import AddTodo from "./components/AddTodo";
    import TextInfo from "./components/TextInfo";
    import Tab from "./components/Tab";
    import List from "./components/List";
    export default {
      components: {List, Tab, TextInfo, AddTodo, Title},
      data:function () {
        return {
          data:[],
          v:1,
        }
      },
      methods:{
        addTodo:function (todo) {
          this.data.push({
            title:todo,
            finished:false,
          })
        },
        delTodo:function (index) {
          this.data.splice(index,1)
        },
        c:function (i) {
          this.v = i;
        }
      }
    }
</script>
