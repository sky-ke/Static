<template>
  <div class="home">
    <Header/>
    <div class="banner" v-show="pc">
      <el-carousel height="600px" direction="vertical" :autoplay="true">
        <el-carousel-item v-for="(banner,index) in banners" :key="index">
          <img :src="banner.url" alt="">
        </el-carousel-item>
      </el-carousel>
    </div>
    <div class="banner" v-show="!pc">
      <el-carousel height="200px" direction="vertical" :autoplay="true">
        <el-carousel-item v-for="(banner,index) in bannersMobile" :key="index">
          <img :src="banner.url" alt="">
        </el-carousel-item>
      </el-carousel>
    </div>
    <div class="product">
      <div class="title">
        <img src="../assets/images/product-title.png" alt="">
      </div>
      <div class="box">
        <div class="item" v-for="(product,index) in products" :key="index">
          <router-link :to="product.path">
            <div class="img-box">
              <img :src="product.url" alt="">
            </div>
            <div class="text">
              <div>{{ product.zh }}</div>
              <div class="en">{{ product.en }}</div>
            </div>
          </router-link>
        </div>
      </div>
    </div>
    <div class="about">
      <div class="box">
        <div class="left">
          <div class="title">
            <img src="../assets/images/about-title.png" alt="">
          </div>
          <div class="text">
            乐博科技有限公司位于广东省汕头市，联合十几年生产经验的实力工厂，在产品设计上不断创新，积极拓展产品线。多年积累的行业经验及技术力量充分保证了产品质量及完善的服务。目前产品包含NTC 元件及温度传感器，各类电器、机械设备及相关...
          </div>
          <a class="btn" href="javascript:void(0)">查看更多</a>
        </div>
        <div class="right">
          <img src="../assets/images/about.jpg" alt="">
        </div>
      </div>
    </div>
    <div class="news">
      <div class="title">
        <img src="../assets/images/news-title.png" alt="">
      </div>
      <div class="box">
        <div class="top">
          <div class="left">
            <img :src="newsTop.url" alt="">
          </div>
          <div class="right">
            <div class="news-title">{{ newsTop.title }}</div>
            <div class="date">{{ newsTop.date }}</div>
            <div class="text">{{ newsTop.text }}</div>
            <router-link :to="newsTop.path">查看详情 >></router-link>
          </div>
        </div>
        <div class="bottom" v-for="(news,index) in newsBottom" :key="index">
          <router-link :to="news.path">
            <div class="main">
              <div class="title">{{ news.title }}</div>
              <div class="text">{{ news.text }}</div>
            </div>
            <div class="go">
              <div class="date">{{ news.date }}</div>
              <div class="icon">
                <img src="../assets/images/go.png" alt="">
              </div>
            </div>
          </router-link>
        </div>
      </div>
    </div>
    <Footer/>
  </div>
</template>

<script>
import Header from '@/components/Header.vue'
import Footer from '@/components/Footer.vue'

export default {
  name: 'Home',
  components: {
    Header,
    Footer
  },
  data() {
    return {
      screenWidth: document.body.clientWidth,
      pc: true,
      banners: [
        {url: require("../assets/images/banner.jpg")},
        {url: require("../assets/images/banner.jpg")},
        {url: require("../assets/images/banner.jpg")}
      ],
      bannersMobile: [
        {url: require("../assets/images/banner-mobile.jpg")},
        {url: require("../assets/images/banner-mobile.jpg")},
        {url: require("../assets/images/banner-mobile.jpg")}
      ],
      products: [
        {url: require("../assets/images/product.jpg"),zh:"NTC热敏电阻温度传感器系列",en:"TJD",path:"/"},
        {url: require("../assets/images/product.jpg"),zh:"NTC热敏电阻温度传感器系列",en:"TJD",path:"/"},
        {url: require("../assets/images/product.jpg"),zh:"NTC热敏电阻温度传感器系列",en:"TJD",path:"/"},
        {url: require("../assets/images/product.jpg"),zh:"NTC热敏电阻温度传感器系列",en:"TJD",path:"/"},
        {url: require("../assets/images/product.jpg"),zh:"NTC热敏电阻温度传感器系列",en:"TJD",path:"/"},
        {url: require("../assets/images/product.jpg"),zh:"NTC热敏电阻温度传感器系列",en:"TJD",path:"/"}
      ],
      newsTop: {
        url: require("../assets/images/news.jpg"),
        title:"中国解决分子压电材料难题,以后可以用衣服给手机充电...",
        date:"2018-03-22",
        text:"从东南大学官网获悉，该校熊仁根教授团队、游雨蒙教授课题组与合作者在分子铁电、压电材料领域取得重要研究进展。文中指出，压电性指的是材料在受挤压或拉伸时可以产生电，或在材料两端施加电压后材料伸长或缩短的特性。",
        path:"/"
      },
      newsBottom: [
        {
          title:"工信部公示200项行标含无损检测",
          date:"2019-02-20",
          text:"工信部公示200项行标含无损检测、试验箱等仪器及分析法.继2017年一大波千余项行业公示后...",
          path:"/"
        },
        {
          title:"9项无损检测新标准2018年开始执行",
          date:"2019-02-20",
          text:"2018年4月1日我们即将迎来一批新的无损检测标准。这次发布的9项由全国无损检测标委会...",
          path:"/"
        },
        {
          title:"ICRA 2017最佳服务机器人论文大盘点",
          date:"2019-02-20",
          text:"雷锋网AI科技评论,是机器人技术领域最有影响力的国际学术会议之一。",
          path:"/"
        }
      ]
    };
  },
  mounted() {
    // console.log(this.screenWidth);
    if(this.screenWidth < 1200){
      this.pc = false;
    }else{
      this.pc = true;
    }
    const that = this;
    window.onresize = () => {
      return (() => {
        window.screenWidth = document.body.clientWidth;
        that.screenWidth = window.screenWidth;
      })();
    };
  },
  watch: {
    screenWidth (val) {
      this.screenWidth = val;
      // console.log(this.screenWidth);
      if(val < 1200){
        this.pc = false;
      }else{
        this.pc = true;
      }
    }
  }
}
</script>

<style scoped lang="scss">
.banner{
  el-carousel{
    height: 600px;
    position: relative;
    overflow: hidden;
  }
  img{
    position: absolute;
    top: 50%;
    left: 50%;
    transform: translate(-50%,-50%);
  }
}
.product{
  padding: 50px 0;
  background-color: #f8f8f8;
  .title{
    margin-bottom: 40px;
    img{
      display: block;
      margin: 0 auto;
    }
  }
  .box{
    .item{
      display: inline-block;
      width: calc((100% - 40px) / 3);
      height: 430px;
      box-sizing: border-box;
      margin-bottom: 20px;
      background-color: #fff;
      &:nth-child(3n+2){
        margin: 0 20px;
      }
      a{
        display: block;
        height: 100%;
        box-sizing: border-box;
        padding: 20px;
        .img-box{
          height: 80%;
          position: relative;
          overflow: hidden;
          img{
            width: 100%;
            position: absolute;
            top: 50%;
            left: 50%;
            transform: translate(-50%,-50%);
            transition: .3s;
          }
        }
        &:hover img{
          width: 110%;
        }
        .text{
          text-align: center;
          font-size: 18px;
          line-height: 1.6;
          padding: 15px 0;
          box-sizing: border-box;
          .en{
            font-size: 14px;
            color: #999;
          }
        }
      }
    }
  }
}
.about{
  padding: 100px 0;
  background-color: #eee;
  .box{
    font-size: 0;
    .left{
      display: inline-block;
      width: 40%;
      box-sizing: border-box;
      padding: 50px 60px 0 20px;
      font-size: 14px;
      .title{
        margin-bottom: 50px;
      }
      .text{
        color: #999;
        line-height: 2;
        margin-bottom: 40px;
      }
      .btn{
        display: inline-block;
        background-color: #3d4bc7;
        border-radius: 24px;
        color: #fff;
        padding: 14px 70px;
      }
    }
    .right{
      display: inline-block;
      width: 60%;
      vertical-align: top;
      img{
        width: 100%;
      }
    }
  }
}
.news{
  padding: 50px 0;
  .title{
    margin-bottom: 40px;
    img{
      display: block;
      margin: 0 auto;
    }
  }
  .top{
    height: 412px;
    font-size: 0;
    background-color: #f8f8f8;
    .left{
      display: inline-block;
      width: 50%;
      height: 100%;
      vertical-align: top;
      position: relative;
      overflow: hidden;
      img{
        width: 100%;
        height: 100%;
        position: absolute;
        top: 50%;
        left: 50%;
        transform: translate(-50%,-50%);
        transition: .3s;
      }
      &:hover img{
        width: 110%;
        height: 110%;
      }
    }
    .right{
      display: inline-block;
      width: 50%;
      height: 100%;
      font-size: 14px;
      padding: 60px;
      box-sizing: border-box;
      line-height: 2;
      .news-title{
        font-size: 18px;
      }
      .date{
        color: #999;
      }
      .text{
        color: #666;
        margin: 30px 0 60px 0;
      }
      a{
        padding: 12px 26px;
        border: 2px solid #b4b4b4;
        &:hover{
          border: 2px solid #3d4bc7;
        }
      }
    }
  }
  .bottom{
    margin-top: 20px;
    display: inline-block;
    width: calc((100% - 40px) / 3);
    box-sizing: border-box;
    &:nth-child(3n+3){
      margin: 0 20px;
    }
    .main{
      padding: 35px 40px;
      background-color: #f8f8f8;
      .title{
        font-size: 18px;
        margin-bottom: 25px;
      }
      .text{
        font-size: 14px;
        line-height: 2;
        color: #666;
      }
    }
    &:hover .main .title{
      color: #3d4bc7;
    }
    .go{
      height: 64px;
      border-top: 1px solid #e9e9e9;
      background-color: #f5f5f5;
      position: relative;
      .date{
        font-size: 14px;
        color: #999;
        position: absolute;
        top: 50%;
        left: 40px;
        transform: translate(0, -50%);
      }
      .icon{
        position: absolute;
        top: 50%;
        right: 40px;
        transform: translate(0, -50%);
      }
    }
  }
}
</style>
