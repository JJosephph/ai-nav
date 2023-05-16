<template>
  <div class="app">
    <el-input v-model="input" placeholder="请输入内容"></el-input>
  </div>
</template>

<script>
export default {
  name: "app",
  data() {
    return {
      input: ''
    };
  },
};
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style>

</style>