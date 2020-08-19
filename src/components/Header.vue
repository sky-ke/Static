<template>
  <div class="Header">
    <div class="container">
      <div class="logo">
        <img src="../assets/images/logo.png" alt="">
      </div>
      <div class="nav">
        <div class="nav-btn"
          :class="{on : nav.value == '首页'}"
          v-for="(nav,index) in navs"
          :key="index">
          <router-link :to="nav.path">{{ nav.value }}</router-link>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: 'Header',
  data() {
    return {
      navs: [
        {value:"首页123",path:"/",on:false},
        {value:"关于我们",path:"/",on:false},
        {value:"产品中心",path:"/",on:false},
        {value:"新闻资讯",path:"/",on:false},
        {value:"联系我们",path:"/",on:false}
      ]
    };
  }
}
</script>

<style scoped lang="scss">
.Header{
  width: 100%;
  height: 100px;
  padding: 12px;
  box-sizing: border-box;
  .container{
    max-width: 1200px;
    margin: 0 auto;
    overflow: hidden;
    position: relative;
    .nav{
      position: absolute;
      top: 50%;
      right: 0;
      transform: translate(0,-50%);
      .nav-btn{
        display: inline-block;
        padding: 8px 25px;
        a:hover{
          color: #3d4bc7;
        }
      }
      .on{
        background-color: #3d4bc7;
        border-radius: 20px;
        a{
          color: #fff !important;
        }
      }
    }
  }
}
</style>
