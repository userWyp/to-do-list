<template>
    <div>
        共有{{count}}个目标，已完成{{finished}}，还有{{count-finished}}条未完成
    </div>
</template>

<script>
  export default {
    name: "TextInfo",
    props:['d'],
    data:function () {
      return {
        data:this.d,
      }
    },
    computed:{
      count:function () {
        return this.data.length
      },
      finished:function () {
        let n=0;
        for (let item of this.data){
          if (item.finished){
            n++;
          }
        }
        return n;
      }
    }
  }
</script>

<style scoped>

</style>