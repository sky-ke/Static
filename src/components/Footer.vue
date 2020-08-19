<template>
  <div class="Footer">
    <div class="container">
      <div class="left">
        <div class="item" v-for="(nav,index) in navs" :key="index">
            <div class="title">{{ nav.title }}</div>
            <router-link :to="nav.path1">
                <div class="sub">{{ nav.sub1 }}</div>
            </router-link>
            <router-link :to="nav.path2">
                <div class="sub">{{ nav.sub2 }}</div>
            </router-link>
        </div>
      </div>
      <div class="right">
          <div>热线电话：</div>
          <div>135-0297-8824</div>
          <div>地址：广东省汕头市东海岸一品湾三期10栋2215 </div>
          <div>邮箱： linda@stlebo.cn</div>
          <div>CopyRight © 2019 汕头市乐博科技有限公司版权所有  备案号：粤ICP123456789</div>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: 'Footer',
  data() {
    return {
      navs: [
        {
            title: "关于我们",
            sub1: "公司简介",path1:"/",
            sub2: "企业荣誉",path2:"/"
        },
        {
            title: "产品中心",
            sub1: "产品分类1",path1:"/",
            sub2: "产品分类2",path2:"/"
        },
        {
            title: "新闻资讯",
            sub1: "公司新闻",path1:"/",
            sub2: "行业资讯",path2:"/"
        },
        {
            title: "联系我们",
            sub1: "联系方式",path1:"/"
        }
        // {value:"产品中心",path:"/",on:false},
        // {value:"新闻资讯",path:"/",on:false},
        // {value:"联系我们",path:"/",on:false}
      ]
    };
  }
}
</script>

<style scoped lang="scss">
.Footer{
  width: 100%;
  height: 250px;
  background-color: #3d4bc7;
  .container{
    max-width: 1200px;
    margin: 0 auto;
    overflow: hidden;
    position: relative;
    padding: 60px 12px 0 12px;
    box-sizing: border-box;
    color: #fff;
    .left{
        float: left;
        .item{
            display: inline-block;
            margin-right: 60px;
            vertical-align: top;
            &:last-child{
                margin-right: 0;
            }
            .title{
                margin-bottom: 30px;
            }
            .sub{
                color: #fff;
                font-size: 14px;
                margin-bottom: 16px;
            }
        }
    }
    .right{
        float: right;
        text-align: right;
        font-size: 14px;
        div{
            &:nth-child(1){
                font-size: 20px;
            }
            &:nth-child(2){
                font-size: 24px;
                font-weight: 600;
                margin: 8px 0;
            }
            &:nth-child(4){
                margin: 8px 0 12px 0;
            }
        }
    }
  }
}
</style>
