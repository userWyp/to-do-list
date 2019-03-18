<template>
    <div>
        <Todo v-for="(item,index) in data" :d="item" :t="t" @del="del(index)"></Todo>
    </div>
</template>

<script>
  import Todo from "./Todo";
  export default {
    name: "List",
    components: {Todo},
    data:function () {
      return {
        data:this.d,
        // v1:this.v
      }
    },
    props:['d','t'],
    methods:{
      del:function (index) {
        this.$emit('del',index);
      }
    }
  }
</script>

<style scoped>

</style>