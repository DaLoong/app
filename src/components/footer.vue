<template>
  <div class="footer">
    <div v-for="item in footer" :key="item.name" class="footer-div">
      {{item.name}}:
      <router-link :to="item.src">{{item.text}}</router-link>
    </div>
    <div class="icp">
      {{icp}}
    </div>
  </div>
</template>

<script>
export default {
  name: "Footer",
  data() {
    return {
      footer: [],
      icp: 'Copyright 2020|京ICP备0000'
    }
  },
  created() {
    // 获取footer菜单
    this.$api.get('getFooter').then((res) => {
      this.footer = res.data
    })
  }

}
</script>

<style scoped>
.footer{
  background: #4a4b4a;
  color: azure;
  min-height: 200px;
  position: relative;
}
.footer a{
  color: aliceblue;
}
.footer-div{
  padding-top: 20px;
}
.icp{
  position: absolute;
  bottom: 10px;
  color: darkgrey;
  width: 100vw;
}
</style>
