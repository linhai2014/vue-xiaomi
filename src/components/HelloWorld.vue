<template>
  <div>
<!--顶部-->
    <div id="top">
      <div class="center">
        <div class="left">
          <a href="">小米商城<span></span></a>
          <a href="">MIUI<span></span></a>
          <a href="">IoT<span></span></a>
          <a href="">云服务<span></span></a>
          <a href="">水滴<span></span></a>
          <a href="">金融<span></span></a>
          <a href="">有品<span></span></a>
          <a href="">Select Region</a>

        </div>
        <div class="right">
          <a href="">登录<span></span></a>
          <a href="">注册<span></span></a>
          <a href="">消息通知</a>
          <div class="cart">
            <a><i class="iconfont icon-shopping-cart"></i>购物车(0)</a>
            <div class="hide">购物车中还没有商品，赶紧选购吧！</div>
          </div>
        </div>
      </div>
    </div>
<!--搜索区域-->
    <div id="search">
      <a href="" class="logo"></a>
      <a href="" class="promotion"><img src="../assets/image/xiaomi618.gif" alt=""/></a>
      <div class="menu">
        <div class="top">
          <a href=""
             v-for="item in this.items"
             :key="item.id"
             @mouseenter="switchSubMenu(item.id)"
             @mouseleave="switchSubMenu(item.id)"
          >
            {{item.title}}
          </a>
          <a href="">服务</a>
          <a href="">社区</a>
        </div>
        <div class="menu-hide">
          <ul>
            <li v-for="item in this.items" :key="item.id" v-show="item.show">
              <div v-for="product in item.products" :key="product.name">
                <p class="hot" v-show="product.hot">{{product.hot}}</p>
                <a href="" class="pic">
                  <img src="../assets/image/xiaomicc.png">
                </a>
                <a href="" class="title">{{product.name}}</a>
                <a href="" class="price">{{product.price}}</a>
              </div>
            </li>
          </ul>
        </div>
      </div>
      <div class="form" :class="{borderOnFocus:showHistory}">
        <input type="text" v-on:focus = "showHistory = true" v-on:blur = "showHistory = false"/>
        <div class="submit">
          <i class="iconfont icon-fangdajing"></i>
        </div>
        <div class="tags" v-show="!showHistory">
          <a href="">红米Note 5</a>
          <a href="">小米MIX 2S 新品发布</a>
        </div>
        <ul v-show="showHistory">
          <li>
            <a href="" class="l">小米手机6</a>
            <a href="" class="r">约有29件</a>
          </li>
          <li>
            <a href="" class="l">小米手机6</a>
            <a href="" class="r">约有29件</a>
          </li>
          <li>
            <a href="" class="l">小米手机6</a>
            <a href="" class="r">约有29件</a>
          </li>
          <li>
            <a href="" class="l">小米手机6</a>
            <a href="" class="r">约有29件</a>
          </li>
          <li>
            <a href="" class="l">小米手机6</a>
            <a href="" class="r">约有29件</a>
          </li>
          <li></li>
        </ul>
      </div>

    </div>
<!--轮播图-->
    <div id="flashbox" @mouseenter="clearTimer" @mouseleave="resetTimer">
      <div class="flash">
        <a class="pic" href="" v-for="page in pages" :key="page.id" v-show="page.id == curPage">
          <img :src= "page.path"  alt=""/>
        </a>

        <ul>
          <li v-for="page in pages"
              :key="page.id"
              :class="{cur:page.id == curPage}"
              @click="clickIndicator(page.id)"
          >
          </li>
        </ul>

        <a class="lbtn" @click="switchBack">
          <i class="iconfont icon-zuo"></i>
        </a>

        <a class="rbtn" @click="switchForward">
          <i class="iconfont icon-you"></i>
        </a>
      </div>
      <ul>
        <li v-for="item in this.leftMenus"
              :key="item.id">
          <a href="" class="left">
            <span>{{item.title}}</span>
            <i class="iconfont icon-you"></i>
          </a>
          <div>
            <ul class="list">
              <li v-for="product in item.products"
                  :key="product.name">
                <a href="">
                  <img src="../assets/image/xiaomiCC9.png"/>
                  <span>{{product.name}}</span>
                </a>
              </li>
            </ul>
          </div>
        </li>
      </ul>
    </div>
<!--重点推荐区域-->
    <div id="hot">
      <ul>
        <li>
          <i class="iconfont icon-naozhong"></i>
          <p>选购手机</p>
          <span class="r"></span>
          <span class="b"></span>
        </li>
        <li>
          <i class="iconfont icon-naozhong"></i>
          <p>选购手机</p>
          <span class="r"></span>
          <span class="b"></span>
        </li>
        <li>
          <i class="iconfont icon-naozhong"></i>
          <p>选购手机</p>
          <span class="b"></span>
        </li>
        <li>
          <i class="iconfont icon-naozhong"></i>
          <p>选购手机</p>
          <span class="r"></span>
        </li>
        <li>
          <i class="iconfont icon-naozhong"></i>
          <p>选购手机</p>
          <span class="r"></span>
        </li>
        <li>
          <i class="iconfont icon-naozhong"></i>
          <p>选购手机</p>
        </li>
      </ul>

      <a href="">
        <img src="../assets/image/p1.jpg"/>
      </a>
      <a href="">
        <img src="../assets/image/p2.jpg"/>
      </a>
      <a href="">
        <img src="../assets/image/p3.jpg"/>
      </a>
    </div>

<!--小米闪购-->
    <div id="fasttitle">
      <p>小米闪购</p>
      <div>
        <a class="first" :class="{disable:disableLeftBtn}" @click="slideLeft">
          <i class="iconfont icon-zuo"></i>
        </a>
        <a class="second" :class="{disable:disableRightBtn}" @click="slideRight">
          <i class="iconfont icon-you"></i>
        </a>
      </div>
    </div>

    <div id="fastcontent">
      <div class="left">
        <p class="begintime">20:00场</p>
        <img src="../assets/image/flashpurchase.png" alt=""/>
        <p class="endtime">距离结束还有</p>
        <div class="time">
          <div>{{hour}}</div>
          <p>:</p>
          <div>{{minute}}</div>
          <p>:</p>
          <div>{{second}}</div>
        </div>
      </div>

      <div class="right">
        <div class="rcontent" :style="slide2Left">
          <div>
            <a class="pic"><img src="../assets/image/phone.jpg"></a>
            <a href="" class="title">上海自来水来自海上 山东落花生花落东山</a>
            <p class="desc">千元全面屏，前置柔光自拍</p>
            <p class="price">1111 <span>8888元</span></p>
          </div>
          <div>
            <a class="pic"><img src="../assets/image/phone.jpg"></a>
            <a href="" class="title">上海自来水来自海上 山东落花生花落东山</a>
            <p class="desc">千元全面屏，前置柔光自拍</p>
            <p class="price">2222 <span>8888元</span></p>
          </div>
          <div>
            <a class="pic"><img src="../assets/image/phone.jpg"></a>
            <a href="" class="title">上海自来水来自海上 山东落花生花落东山</a>
            <p class="desc">千元全面屏，前置柔光自拍</p>
            <p class="price">3333元 <span>8888元</span></p>
          </div>
          <div>
            <a class="pic"><img src="../assets/image/phone.jpg"></a>
            <a href="" class="title">上海自来水来自海上 山东落花生花落东山</a>
            <p class="desc">千元全面屏，前置柔光自拍</p>
            <p class="price">4444元 <span>8888元</span></p>
          </div>
          <div>
            <a class="pic"><img src="../assets/image/phone.jpg"></a>
            <a href="" class="title">上海自来水来自海上 山东落花生花落东山</a>
            <p class="desc">千元全面屏，前置柔光自拍</p>
            <p class="price">5555元 <span>8888元</span></p>
          </div>
          <div>
            <a class="pic"><img src="../assets/image/phone.jpg"></a>
            <a href="" class="title">上海自来水来自海上 山东落花生花落东山</a>
            <p class="desc">千元全面屏，前置柔光自拍</p>
            <p class="price">6666元 <span>8888元</span></p>
          </div>
        </div>
      </div>
    </div>

<!--Banner-->
    <a href="" class="heisha">
      <img src="../assets/image/banner.png">
    </a>

<!--大灰色区域-->
    <div id="greybox">
      <div class="titlebox">
        <p>手机</p>
        <a href=""><span>查看全部</span><i class="iconfont icon-you"></i></a>
      </div>
      <div class="mobile">
        <a href="">
          <img src="../assets/image/left.png">
        </a>
        <ul>
          <li>
            <div>
              <a class="pic"><img src="../assets/image/phone.jpg"></a>
              <a href="" class="title">上海自来水来自海上 山东落花生花落东山</a>
              <p class="desc">千元全面屏，前置柔光自拍</p>
              <p class="price">1111 <span>8888元</span></p>
              <p class="top">减100元</p>
              <a class="bot">
                <span>特用了一段时间才来评价的，电视性能特别好，更值得赞的...</span>
                <span>来自于 邓治江 的评价</span>
              </a>
            </div>
          </li>
          <li>
            <div>
              <a class="pic"><img src="../assets/image/phone.jpg"></a>
              <a href="" class="title">上海自来水来自海上 山东落花生花落东山</a>
              <p class="desc">千元全面屏，前置柔光自拍</p>
              <p class="price">1111 <span>8888元</span></p>
              <p class="top">减100元</p>
            </div>
          </li>
          <li>
            <div>
              <a class="pic"><img src="../assets/image/phone.jpg"></a>
              <a href="" class="title">上海自来水来自海上 山东落花生花落东山</a>
              <p class="desc">千元全面屏，前置柔光自拍</p>
              <p class="price">1111 <span>8888元</span></p>
              <p class="top">减100元</p>
            </div>
          </li>
          <li>
            <div>
              <a class="pic"><img src="../assets/image/phone.jpg"></a>
              <a href="" class="title">上海自来水来自海上 山东落花生花落东山</a>
              <p class="desc">千元全面屏，前置柔光自拍</p>
              <p class="price">1111 <span>8888元</span></p>
              <p class="top">减100元</p>
            </div>
          </li>
          <li>
            <div>
              <a class="pic"><img src="../assets/image/phone.jpg"></a>
              <a href="" class="title">上海自来水来自海上 山东落花生花落东山</a>
              <p class="desc">千元全面屏，前置柔光自拍</p>
              <p class="price">1111 <span>8888元</span></p>
              <p class="top">减100元</p>
            </div>
          </li>
          <li>
            <div>
              <a class="pic"><img src="../assets/image/phone.jpg"></a>
              <a href="" class="title">上海自来水来自海上 山东落花生花落东山</a>
              <p class="desc">千元全面屏，前置柔光自拍</p>
              <p class="price">1111 <span>8888元</span></p>
              <p class="top">减100元</p>
            </div>
          </li>
          <li>
            <div>
              <a class="pic"><img src="../assets/image/phone.jpg"></a>
              <a href="" class="title">上海自来水来自海上 山东落花生花落东山</a>
              <p class="desc">千元全面屏，前置柔光自拍</p>
              <p class="price">1111 <span>8888元</span></p>
              <p class="top">减100元</p>
            </div>
          </li>
          <li>
            <div>
              <a class="pic"><img src="../assets/image/phone.jpg"></a>
              <a href="" class="title">上海自来水来自海上 山东落花生花落东山</a>
              <p class="desc">千元全面屏，前置柔光自拍</p>
              <p class="price">1111 <span>8888元</span></p>
              <p class="top">减100元</p>
            </div>
          </li>
        </ul>
      </div>
    </div>
  </div>
</template>

<script>
  import $ from 'jquery'

  export default {
  name: 'HelloWorld',
  data() {
    return{
      disableLeftBtn:false,
      disableRightBtn:false,
      slideIndex:0,
      secondKill:4763000,
      curPage:0,
      timerID:0,
       // vue中v-for图片src路径错误
       // https://blog.csdn.net/m0_37605642/article/details/90447322
      pages:[
        {id:"0", path:require('../assets/image/1.jpg')},
        {id:"1", path:require('../assets/image/2.jpg')},
        {id:"2", path:require('../assets/image/3.jpg')},
        {id:"3", path:require('../assets/image/4.jpg')}
      ],
      showHistory:false,
      items: [
        { id: 1, title:"小米手机", show:true, products:[
            {hot:"热卖", name:"小米MIX 2", price:"2007元"},
            {name:"荣耀 2", price:"2020元"},
            {hot:"热卖", name:"iPhoneX", price:"3000元"},
            {name:"OPPO", price:"2000元"}
          ]
        },
        { id: 2, title:"荣耀", show:false, products:[
            {hot:"热卖", name:"红米 2", price:"1000元"},
            {name:"格里", price:"2020元"},
            {hot:"热卖", name:"VIVO", price:"4000元"},
          ]
        },
        { id: 3, title:"电视", show:false, products:[
            {}
          ] },
        { id: 4, title:"笔记本", show:false, products:[
            {}
          ] },
        { id: 5, title:"家电", show:false, products:[
            {}
          ] },
        { id: 6, title:"路由器", show:false, products:[
            {}
          ] },
        { id: 7, title:"智能硬件", show:false, products:[
            {}
          ]
        },
      ],
      leftMenus:[
        {id:1, title:"手机 电话卡", products:[
            { name:"小米MIX 1S"},
            { name:"小米MIX 2S"},
            { name:"小米MIX 3S"},
            { name:"小米MIX 4S"},
            { name:"小米MIX 5S"},
            { name:"小米MIX 6S"},
            { name:"小米MIX 7S"},
            { name:"小米MIX 8S"},
            { name:"小米MIX 9S"},
            { name:"小米MIX X1"},
            { name:"小米MIX X2"},
            { name:"小米MIX X3"}
          ]},
        {id:1, title:"苹果 旗舰机", products:[
            { name:"苹果 1S"},
            { name:"苹果 2S"},
            { name:"苹果 3S"},
            { name:"苹果 4S"},
            { name:"苹果 5S"},
            { name:"小米MIX 6S"},
            { name:"小米MIX 7S"},
            { name:"小米MIX 8S"},
            { name:"小米MIX 9S"},
            { name:"小米MIX X1"},
            { name:"小米MIX X2"},
            { name:"小米MIX X3"}
          ]},
        {id:1, title:"手机 电话卡", products:[
            { name:"小米MIX 1S"},
            { name:"小米MIX 2S"},
            { name:"小米MIX 3S"},
            { name:"小米MIX 4S"},
            { name:"小米MIX 5S"},
            { name:"小米MIX 6S"},
            { name:"小米MIX 7S"},
            { name:"小米MIX 8S"},
            { name:"小米MIX 9S"},
            { name:"小米MIX X1"},
            { name:"小米MIX X2"},
            { name:"小米MIX X3"}
          ]},
        {id:1, title:"手机 电话卡", products:[
            { name:"小米MIX 1S"},
            { name:"小米MIX 2S"},
            { name:"小米MIX 3S"},
            { name:"小米MIX 4S"},
            { name:"小米MIX 5S"},
            { name:"小米MIX 6S"},
            { name:"小米MIX 7S"},
            { name:"小米MIX 8S"},
            { name:"小米MIX 9S"},
            { name:"小米MIX X1"},
            { name:"小米MIX X2"},
            { name:"小米MIX X3"}
          ]},
        {id:1, title:"手机 电话卡", products:[
            { name:"小米MIX 1S"},
            { name:"小米MIX 2S"},
            { name:"小米MIX 3S"},
            { name:"小米MIX 4S"},
            { name:"小米MIX 5S"},
            { name:"小米MIX 6S"},
            { name:"小米MIX 7S"},
            { name:"小米MIX 8S"},
            { name:"小米MIX 9S"},
            { name:"小米MIX X1"},
            { name:"小米MIX X2"},
            { name:"小米MIX X3"}
          ]},
        {id:1, title:"手机 电话卡", products:[
            { name:"小米MIX 1S"},
            { name:"小米MIX 2S"},
            { name:"小米MIX 3S"},
            { name:"小米MIX 4S"},
            { name:"小米MIX 5S"},
            { name:"小米MIX 6S"},
            { name:"小米MIX 7S"},
            { name:"小米MIX 8S"},
            { name:"小米MIX 9S"},
            { name:"小米MIX X1"},
            { name:"小米MIX X2"},
            { name:"小米MIX X3"}
          ]}
      ]
    }
  },
  props: {
  },
  computed:{
    slide2Left(){
      //动态样式
      // https://blog.csdn.net/swiftlinlei/article/details/81507205
      let arr = new Array();
      if (this.slideIndex <= 6 - 4){
        arr.push('transform:');
        // .rcontent > div { width(234) + margin-right(14) } == 248
        arr.push('translateX('+this.slideIndex*(-248)+'px) ');
      }

      return arr.join("");
    },
    slide2Right(){
      let arr = new Array();
      if (this.slideIndex <= 6 - 2){
        arr.push('transform:');
        arr.push('translateX('+this.slideIndex*(248)+'px) ');
      }

      return arr.join("");
    },
    hour(){
      return parseInt(this.secondKill/(60*60*1000));
    },
    minute(){
      let remainSeconds = this.secondKill%(60*60*1000);
      return parseInt(remainSeconds/(60*1000));
    },
    second(){
      let remainSeconds = this.secondKill%(60*60*1000);
      remainSeconds = remainSeconds%(60*1000);
      return parseInt(remainSeconds/1000);
    }
  },
  methods:{
    slideLeft(){
      if (this.disableLeftBtn){
        return;
      }

      this.disableRightBtn = false;

      if (++this.slideIndex == 6 - 4){
        this.disableLeftBtn = true;
      }
    },
    slideRight(){
      if (this.disableRightBtn){
        return;
      }

      this.disableLeftBtn = false;

      if (--this.slideIndex == 0){
        this.disableRightBtn = true;
      }
    },
    switchSubMenu(id){
      this.items.forEach((item)=>{

        item.show = false

        if (item.id == id){
          item.show = true
        }
      })
    },
    switchBack(){
      // alert(this.curPage);
      this.curPage = --this.curPage == -1 ? 3 : this.curPage;
    },
    switchForward(){
      this.curPage = ++this.curPage == 4 ? 0 : this.curPage;
    },
    clearTimer(){
      clearInterval(this.timerID);
    },
    resetTimer(){
      this.timerID = setInterval(() => {
        this.switchForward();
      }, 1000);
    },
    clickIndicator(index){
      this.curPage = index;
    }
  },
  mounted() {
    /**
     *  设置Vue和jQuery共用：
     *  https://www.jianshu.com/p/0005487ee299
     *  https://www.cnblogs.com/lhyhappy365/p/9263159.html
     */

    $("#search .menu .menu-hide")
              .width($('body').width())
              .css('left', -$("#search .menu-hide").offset().left);

    this.resetTimer();

    setInterval(()=>{
      this.secondKill = this.secondKill - 1000
    }, 1000);
  }
}
</script>

<style scoped lang="less">
  *{
    margin: 0;
    padding: 0;
  }

  a{
    text-decoration: none;
  }

  ul{
    li{
      list-style: none;
    }
  }

  #top{
    width: 100%;
    height: 40px;
    background: #333333;

    .center{
      width: 1226px;
      background: #333333;
      height: 40px;
      /*border: 0.5px solid yellow;*/
      margin: 0 auto;
      /*overflow: hidden;*/

      .left{
        width: 545px;
        height: 40px;
        /*border-right: 4px solid pink;*/
        float: left;

        a{
          line-height: 40px;
          font-size: 12px;
          color: #b0b0b0;
          padding: 0 10px;
          /*border: 1px solid white;*/
          display: block;
          height: 40px;
          float: left;
          position: relative;

          span{
            display: block;
            width: 1px;
            height: 12px;
            background: #b0b0b0;
            position: absolute;
            right: 0;
            top: 14px;
          }
        }
      }

      .right{
        float: right;
        /*border-left: 3px solid orange;*/
        height: 40px;

        a{
          line-height: 40px;
          font-size: 12px;
          color: #b0b0b0;
          padding: 0 10px;
          /*border: 1px solid white;*/
          display: block;
          height: 40px;
          float: left;
          position: relative;

          span{
            display: block;
            width: 1px;
            height: 12px;
            background: #b0b0b0;
            position: absolute;
            right: 0;
            top: 14px;
          }
        }

        .cart{
          float: left;
          width: 120px;
          height: 40px;
          background: #424242;
          line-height: 40px;
          text-align: center;
          color: #b0b0b0;
          font-size: 12px;
          position: relative;
          z-index: 50;

          a{
            display: block;
            width: 100%;
            box-sizing: border-box;
          }

          &:hover{
            .hide{
              /*display: block;*/
              height: 98px;
            }

            a{
              color: #ff6700;
              background: white;
              height: 41px;
              position: relative;
              z-index: 99;
            }
          }

          i{
            margin-right: 4px;
          }

          .hide{
            width: 316px;
            height: 0;
            /*height: 98px;*/
            background: white;
            position: absolute;
            right: 0;
            top: 40px;
            box-shadow: 0 2px 10px rgba(0, 0, 0, 0.15);
            line-height: 98px;
            text-align: center;
            font-size: 12px;
            color: #424242;
            overflow: hidden;
            transition: height 0.2s;
            /*display: none;*/
          }
        }
      }
    }
  }

  #search{
    width: 1226px;
    height: 100px;
    /*border: 1px solid purple;*/
    border-top: none;
    margin: 0 auto;
    position: relative;
    z-index: 40;

    .logo{
      display: block;
      width: 55px;
      height: 55px;
      background: url("../assets/image/xiaomi.jpg") no-repeat center center;
      position: absolute;
      top: 22px;
      left: 0;
    }

    .promotion{
      display: block;
      width: 165px;
      height: 55px;
      position: absolute;
      left: 70px;
      top: 22px;
    }

    .menu{
      width: 660px;
      height: 100px;
      position: absolute;
      top: 0;
      left: 240px;
      z-index: 99;

      &:hover{
        .menu-hide{
          height:229px;

          border-top: #e0e0e0 1px solid;
          border-bottom: #e0e0e0 1px solid;
          box-shadow: 0 1px 1px rgba(0, 0, 0, 0.1);
        }
      }

      .top{
        display: block;
        width: 660px;
        height: 100px;

        a{
          display: block;
          height: 100px;
          line-height: 100px;
          font-size: 16px;
          float: left;
          padding: 0 10px;
        }
      }

      .menu-hide{
        width: 100%;
        height: 0;
        position: absolute;
        top: 100px;
        transition: height 0.2s;
        overflow: hidden;

        border-top: white 0 solid;
        border-bottom: white 0 solid;
        box-shadow: 0 0 0 rgba(0, 0, 0, 0);
        background: white;

        ul{
          width: 1226px;
          height: 229px;
          /*background: pink;*/
          margin: 0 auto;
          position: relative;

          li{
            list-style: none;
            width: 1226px;
            height: 229px;
            position: absolute;
            left: 0;
            top: 0;

            /**
            *   css3操作选择器，排除最后一个元素样式
            *   http://blog.54zm.com/article/138
            */

            div:not(:last-child) a.pic{
              border-right: 1px solid #e0e0e0;
            }

            >div{
              width: 204px;
              height: 100%;
              /*background: yellow;*/
              float: left;
              position: relative;

              .hot{
                /*width: 64px;*/
                padding: 0 20px;
                height: 20px;
                line-height: 20px;
                border: 1px solid;
                font-size: 12px;
                color: #ff6700;

                position: absolute;
                left: 50%;
                top: 0;
                transform: translateX(-50%);
              }

              a.pic{
                display: block;
                width: 100%;
                height: 110px;
                text-align: center;
                margin-top: 42px;

                img{
                  height: 110px;
                }
              }

              a.title{
                font-size: 12px;
                line-height: 20px;
                display: block;
                text-align: center;
                color: #333;
                margin-top: 23px;
              }

              a.price{
                font-size: 12px;
                line-height: 20px;
                display: block;
                text-align: center;
                color: #ff6700;
              }
            }
          }
        }
      }
    }

    .form{
      width: 294px;
      height: 48px;
      border: 1px solid #e0e0e0;
      position: absolute;
      right: 0;
      top: 25px;

      >input{

        &:focus{
          outline: none;
          border-color: #ff6700;
        }

        /*box-sizing: border-box;*/
        width: 233px;
        height: 48px;
        /*background: blue;*/
        border: none;
        border-right: 1px solid #e0e0e0;
        float: left;

        /**
         * css 调整input内文字与光标的初始位置
         * https://blog.csdn.net/qq_31424825/article/details/85084851
         */
        padding-left: 10px;
      }

      .submit{
        width: 50px;
        height: 48px;
        float: right;

        &:hover{
          background: #ff6700;
          i{
            color: white;
          }
        }

        display: flex;
        justify-content: center;
        align-items: center;

        i{
          color: #616161;
          font-size: 18px;
        }
      }

      .tags{
        height: 18px;
        position: absolute;
        top: 15px;
        right: 61px;

        a{
          padding: 0 5px;
          background: #eeeeee;
          display: block;
          height: 18px;
          float: left;
          font-size: 12px;
          color: #757575;
          margin-left: 5px;
        }
      }

      >ul{
        width: 243px;
        border: 1px solid #ff6700;
        border-top: none;
        position: absolute;
        left: -1px;
        top: 49px;
        background: white;

        li{
          list-style: none;

          &:hover >a{
            background: #fafafa;
          }

          a{
            display: block;
            height: 30px;
            line-height: 30px;
            font-size: 12px;

            &.l{
              width: 106px;
              padding-left: 15px;
              float: left;
              color: #424242;
            }

            &.r{
              width: 106px;
              padding-right: 15px;
              float: right;
              text-align: right;
              color: #b0b0b0;
            }
          }
        }
      }
    }

    .borderOnFocus{
      border-color: #ff6700;
    }
  }

  #flashbox{
    width: 1226px;
    height: 460px;
    /*border: 1px solid blue;*/
    margin: 0 auto;
    position: relative;
    z-index: 20;

    .flash{
      width: 1226px;
      height: 460px;
      position: absolute;
      left: 0;
      top: 0;
      z-index: 20;

      a.pic{
        display: block;
        width: 1226px;
        height: 460px;
        position: absolute;
        left: 0;
        top: 0;

        img{
          width: 100%;
          height: 100%;
        }
      }

      ul{
        position: absolute;
        right: 35px;
        bottom: 25px;

        li{
          list-style: none;
          width: 6px;
          height: 6px;
          float: left;
          background: rgba(0, 0, 0, 0.4);
          border-radius: 50%;
          margin-left: 10px;
          border: 2px solid rgba(117, 117, 117, 0.3);

          &.cur{
            background: rgba(255, 255, 255, 0.4);
          }
        }
      }

      .lbtn{
        position: absolute;
        width: 41px;
        height: 69px;
        /*border: 1px solid blue;*/
        left: 234px;
        top:195px;
        display: block;
        /*z-index: 30;*/

        i{
          font-size: 35px;
          color: rgba(255, 255, 255, 0.6);
          position: absolute;
          left: 50%;
          top: 50%;
          transform: translate(-50%, -50%);
        }

        &:hover{
          background: rgba(0, 0, 0, 0.2);
        }
      }

      .rbtn{
        display: block;
        width: 41px;
        height: 69px;
        /*border: 1px solid blue;*/
        position: absolute;
        right: 0px;
        top:195px;
        /*z-index: 30;*/

        i{
          font-size: 35px;
          color: rgba(255, 255, 255, 0.6);
          position: absolute;
          left: 50%;
          top: 50%;
          transform: translate(-50%, -50%);
        }

        &:hover{
          background: rgba(0, 0, 0, 0.2);
        }
      }
    }

    >ul{
      width: 234px;
      height: 460px;
      position: absolute;
      left: 0;
      top: 0;
      background: rgba(0, 0, 0, 0.6);
      z-index: 30;
      >li{
        width: 100%;
        height: 42px;

        &:hover{
          background: #ff6700;
        }

        >a{
          width: 100%;
          height: 42px;
          /*background: pink;*/
          display: block;

          span{
            line-height: 42px;
            font-size: 14px;
            color: white;
            float: left;
            text-indent: 29px;
          }

          i{
            line-height: 42px;
            font-size: 14px;
            float: right;
            color: rgba(255, 255, 255, 0.5);
            padding-right: 25px;
          }
        }

        >div{
          width: 532px;
          height: 460px;
          border: 1px solid #e0e0e0;
          position: absolute;
          left: 234px;
          top: 0;
          display: none;
          box-shadow: 0 8px 16px rgba(0, 0, 0, 0.18);
          background: white;

          ul.list{
            width: 532px;
            height: 460px;
            /*float: left;*/
            /*border-right: 1px solid blue;*/

            li{
              width: 266px;
              height: 75px;
              float: left;
              /*border-bottom: 1px solid black;*/

              a{
                display: block;
                width: 100%;
                height: 100%;
                /*background: yellow;*/
                position: relative;

                img{
                  max-width: 35px;
                  max-height: 40px;
                  position: absolute;
                  left: 26px;
                  top: 50%;
                  transform: translateY(-50%);
                }

                span{
                  line-height: 75px;
                  font-size: 14px;
                  font-weight: 500;
                  color: #333;
                  text-indent: 71px;
                  display: block;

                  &:hover{
                    color: #ff3c00;
                  }
                }
              }
            }
          }
        }

        &:hover > div{
          display: block;
        }
      }
    }
  }

  #hot{
    width: 1226px;
    height: 170px;
    /*border: 1px solid blue;*/
    margin: 14px auto;

    >ul{
      width: 234px;
      height: 170px;
      background: #575750;
      float: left;

      >li{
        float: left;
        width: 78px;
        height: 85px;
        /*border: 1px solid yellow;*/
        display: flex;
        flex-direction: column;
        justify-content: center;
        align-items: center;
        position: relative;

        i{
          color: rgba(255, 255, 255, 0.7);
          font-size: 25px;
        }

        p{
          color: rgba(255, 255, 255, 0.7);
          font-size: 12px;
          padding-top: 10px;
        }

        span.r{
          display: block;
          width: 1px;
          height: 70px;
          position: absolute;
          right: 0;
          top: 9px;
          background: #665e57;
        }

        span.b{
          display: block;
          width: 64px;
          height: 1px;
          position: absolute;
          bottom: 0;
          left: 6px;
          background: #665e57;
        }
      }
    }

    >a{
      display: block;
      width: 316px;
      height: 170px;
      float: left;
      /*border: 1px solid blue;*/
      margin-left: 14px;

      img{
        width: 100%;
        height: 100%;
      }
    }
  }

  #fasttitle{
    width: 1226px;
    height: 58px;
    /*border: 1px solid blue;*/
    margin: 0 auto;
    margin-top: 26px;

    p{
      font-size: 22px;
      color: #333;
      line-height: 58px;
      float: left;
    }

    div{
      /*width: 69px;*/
      /*height: 22px;*/
      border: 1px solid #e0e0e0;
      float: right;
      margin-top: 24px;

      a{
        display: block;
        width: 34px;
        height: 22px;
        float: left;

        text-align: center;
        line-height: 22px;

        &.first{
          border-right: 1px solid #e0e0e0;
        }

        i{
          font-size: 15px;
          color: #b0b0b0;
          &:hover{
            color: orangered;
          }
        }

        &.disable{
          i{
            color: #e0e0e0;
          }
        }
      }
    }
  }

  #fastcontent{
    width: 1226px;
    height: 340px;
    /*border: 1px solid blue;*/
    margin: 0 auto;

    .left{
      width: 234px;
      height: 339px;
      background: #f1eded;
      border-top: 1px solid #e53935;
      float: left;

      .begintime{
        color: #ef3a3b;
        font-size: 21px;
        line-height: 30px;
        height: 30px;
        text-align: center;
        margin-top: 54px;
      }

      .endtime{
        color: rgba(0, 0, 0, 0.54);
        font-size: 15px;
        line-height: 20px;
        height: 20px;
        text-align: center;
        margin-top: 30px;
      }

      .time{
        width: 168px;
        height: 46px;
        margin: 0 auto;
        /*border: 1px solid orange;*/
        margin-top: 30px;

        div{
          float: left;
          width: 46px;
          height: 46px;
          background: #605751;
          font-size: 24px;
          color: white;
          text-align: center;
          line-height: 46px;
        }

        p{
          float: left;
          font-size: 28px;
          color: #605751;
          text-align: center;
          line-height: 46px;
          height: 46px;
          width: 15px;
        }
      }

      >img{
        display: block;
        margin: 0 auto;
        margin-top: 26px;
      }
    }

    .right{
      width: 978px;
      height: 340px;
      float: right;
      /*background: pink;*/
      position: relative;
      overflow: hidden;

      .rcontent{
        width: 2984px;
        height: 340px;
        position: absolute;
        left: 0;
        top: 0;
        transition: 0.2s;

        >div{
          width: 234px;
          height: 339px;
          border-top: 1px solid #ffac13;
          float: left;
          margin-right: 14px;
          background: rgba(0, 0, 0, 0.02);

          .price{
            text-align: center;
            color: #ff6709;
            font-size: 14px;
            line-height: 22px;
            margin-top: 10px;

            span{
              color: #b0b0b0;
              text-decoration: line-through;
            }
          }

          .desc{
            text-align: center;
            width: 100%;
            font-size: 12px;
            color: #b0b0b0;
            line-height: 20px;
            margin-top: 3px;
          }

          .title{
            display: block;
            width: 194px;
            height: 20px;
            margin: 0 auto;
            margin-top: 36px;
            font-size: 14px;
            color: #212121;
            text-align: center;
            /*border: 1px solid blue;*/

            //文字溢出省略
            white-space:nowrap;
            overflow: hidden;
            text-overflow: ellipsis;
          }

          .pic {
            display: block;
            width: 100%;
            height: 160px;
            text-align: center;
            margin-top: 40px;

            img{
              width: 160px;
              height: 160px;
              //CSS3图片混合模式 正片叠底
              mix-blend-mode: multiply;
            }
          }
        }
      }
    }
  }

  .heisha{
    display: block;
    margin: 0 auto;
    width: 1226px;
    height: 120px;
    margin-top: 42px;

    img{
      width: 100%;
      height: 100%;

    }
  }

  #greybox{
    width: 100%;
    background: #f5f5f5;
    padding-top: 48px;

    .titlebox{
      width: 1226px;
      height: 46px;
      /*border: 1px solid blue;*/
      margin: 0 auto;

      p{
        font-size: 22px;
        color: #333;
        float: left;
        line-height: 46px;
      }

      a{
        float: right;
        font-size: 12px;
        line-height: 46px;
        color: #424242;

        span{
          float: left;
        }

        i{
          float: left;
          display: block;
          border-radius: 50%;
          background: #b0b0b0;
          color: white;
          text-align: center;
          width: 18px;
          height: 18px;
          line-height: 18px;
          font-size: 6px;
          position: relative;
          top: 14px;
          left: 0;
          margin-left: 8px;
        }
      }
    }

    .mobile{
      width: 1226px;
      height: 614px;
      margin: 0 auto;
      /*border: 1px solid blue;*/

      >a{
        display: block;
        height: 614px;
        width: 234px;
        float: left;

        img{
          width: 100%;
          height: 100%;

        }
      }

      >ul{
        width: 992px;
        float: right;
        height: 614px;
        /*background: yellow;*/

        li{
          background: white;
          float: left;
          margin-left: 14px;
          width: 234px;
          height: 300px;
          position: relative;
          margin-bottom: 14px;
          transition: all 0.3s linear;
          /*需要实现运动效果的样式必须有初始值*/
          top:0;
          overflow: hidden;

          &:hover{
            top: -3px;
            box-shadow: 0 15px 30px rgba(0, 0, 0, 0.1);
            transform: translate3d(0, -2px, 0);
          }

          &:hover .bot{
            bottom: 0;
          }

          >div{
            width: 234px;
            height: 339px;
            float: left;
            margin-right: 14px;
            background: rgba(0, 0, 0, 0.02);

            p.top{
              position: absolute;
              top:0;
              left: 50%;
              transform: translateX(-50%);
              height: 20px;
              background: #e53935;
              color: white;
              padding: 0 10px;
              font-size: 12px;
              line-height: 20px;
            }

            .bot{
              width: 100%;
              height: 76px;
              background: #ff6700;
              position: absolute;
              left: 0;
              bottom: -76px;
              transition: all 0.2s linear;

              span{
                font-size: 12px;
                line-height: 20px;
                color: white;
                position: absolute;
                left: 10px;
                width: 214px;
              }

              span:first-child{
                top: 10px;
              }

              span:last-child{
                top: 50px;
              }
            }

            .price{
              text-align: center;
              color: #ff6709;
              font-size: 14px;
              line-height: 22px;
              margin-top: 10px;

              span{
                color: #b0b0b0;
                text-decoration: line-through;
              }
            }

            .desc{
              text-align: center;
              width: 100%;
              font-size: 12px;
              color: #b0b0b0;
              line-height: 20px;
              margin-top: 3px;
            }

            .title{
              display: block;
              width: 194px;
              height: 20px;
              margin: 0 auto;
              margin-top: 25px;
              font-size: 14px;
              color: #212121;
              text-align: center;
              /*border: 1px solid blue;*/

              //文字溢出省略
              white-space:nowrap;
              overflow: hidden;
              text-overflow: ellipsis;
            }

            .pic {
              display: block;
              width: 100%;
              height: 160px;
              text-align: center;
              margin-top: 20px;

              img{
                width: 160px;
                height: 160px;
                //CSS3图片混合模式 正片叠底
                mix-blend-mode: multiply;
              }
            }
          }
        }
      }
    }
  }
</style>
