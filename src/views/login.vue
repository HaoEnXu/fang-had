<template>
  <div class="cover">
    <span class="login" @click="login">登录</span>
  </div>
</template>

<script type='text/ecmascript-6'>
export default {
  data() {
    return {};
  },
  methods: {
    login: function() {
        this.$router.push('/home')
    }
  }
};
</script>

<style lang='less' scoped='' type='text/css'>
.cover {
  position: relative;
  width: 100%;
  height: 100%;
  .login {
    display: inline-block;
    width: 200px;
    height: 50px;
    border-radius: 25px;
    background-color: #b89292;
    color: #000;
    font-weight: bold;
    font-size: 20px;
    line-height: 50px;
    text-align: center;
    cursor: pointer;
    position: absolute;
    top: 50%;
    left: 50%;
    transform: translate(-50%, -50%);
    transition: all 0.3s;
    &:hover {
      background-color: rgb(143, 92, 92);
      color: rgb(199, 198, 198);
    }
  }
}
</style>