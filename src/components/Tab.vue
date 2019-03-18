<template>
    <div>
        <label>
            <input type="radio" value="1" v-model="v"/>
            所有目标
        </label>
        <label>
            <input type="radio" value="2" v-model="v"/>
            已完成目标
        </label>
        <label>
            <input type="radio" value="3" v-model="v"/>
            未完成目标
        </label>
    </div>
</template>

<script>
  export default {
    name: "Tab",
    props:['d'],
    data:function () {
      return {
        v:this.d
      }
    },
    watch:{
      v:function () {
        this.$emit('change1',this.v)
      }
    }
  }
</script>

<style scoped>
</style>