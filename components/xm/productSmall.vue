<template>
    <div class="page-tabbar">
        <div class="page-wrap">
            <div class="backTo">
             <span v-on:click="back">＜</span>
             <h2>运动功能饮料</h2>
             <router-link :to="{path:'/Index'}"><img src="../../assets/im.jpg" alt=""></router-link>
            </div>
            <!-- 02:48px占位符 -->
            <div style="margin-top:48px;"></div>
            <!-- 轮播子组件 -->
            <smaller></smaller>
            <!--导航栏 -->
            <div class="span">
            <h1>运动功能饮料</h1>
            <p>价格: </p>
            <h2>$88</h2>
            <h6>积分:3000</h6>
            </div>
            <ul class="ul">
                <li>销量</li>
                <li>库存</li>
                <li>订单</li>
                <li>评价</li>
            </ul>
            <div class="size">
               <p>尺寸</p>
               <span>S M L XL XXL</span>
               <h4>数量</h4>
               <button v-on="btn">-</button><input type="number" value="1"><button v-on="btn">+</button>
            </div>
            <hr>
            <div class="bt">
                <button class="bt1">加入购物车</button>
                <button class="bt2">立即购买</button>
            </div>
            <div class="map">
                <h1>商家信息</h1>
                <p>地址：杭州市西湖区文西街道66号</p>
                <h5> <img src="../../assets/ic_shake.png" alt=""> 电话联系</h5>
            </div>
            <ul class="adress">
                <li><router-link :to="{path:'/Index'}"><img src="../../assets/m1.png" alt=""></router-link><p>进店逛逛</p></li>
                <li><router-link :to="{path:'/Index'}"><img src="../../assets/m2.png" alt=""></router-link><p>联系卖家</p></li>
            </ul>
            <div>
            <div class="navlist">
           <ul>
             <li class="navli" v-for="(item,index) in navList" :class="{'activeT':nowIndex===index}" @click="tabClick(index)" :key=index><i>{{item.name}}</i>
           </li>
            </ul>
           </div>
           <div class="swiper-container swiper_con">
             <div class="swiper-wrapper">
              <!-- 第一个swiper -->
             <div class="swiper-slide" ref="viewBox">【青春】那时候有多好，任雨打湿裙角。忍不住哼起，心爱的旋律。绿油油的树叶，自由地在说笑。燕子忙归巢，风铃在舞蹈。经过青春的草地，彩虹忽然升起。即使视线渐渐模糊，它也在我心里。就像爱过的旋律，没人能抹去。因为生命存在失望，歌唱，所以才要歌唱。
           </div>
           <!-- 第二个swiper--> 
            <div class="swiper-slide">
           </div>
          </div>
        </div>
       </div>
        </div>
    </div>
</template>

<script>
import smaller from "./common/smaller.vue"
export default {
     name: "swiper",
    data(){ 
        return{
        /*selected:"product",*/
        isShow:false,
        navList:[
     {name:'详情'},
     {name:'交易记录'},
     {name:'评价'}
    ],
    nowIndex:0,
        }
    },
     mounted() {
    var that=this
    that.mySwiper = new Swiper('.swiper-container',{
     initialSlide:0,
     autoplay:false,
     keyboardControl:true,
     autoHeight:true,
     observer:true,
     observeParents:true,
     onSlideChangeStart:function(){
      // console.log(that.mySwiper.activeIndex)
      that.nowIndex=that.mySwiper.activeIndex
     }
    });
   // this.getList();
  },
    components:{
        //"titlebar":TitleBar,
        "smaller":smaller
    },
    methods:{
        back(){
        this.$router.go(-1);//返回上一层
     },  
          tabClick(index){
    this.nowIndex = index
    this.mySwiper.slideTo(index,1000,false)
   },
 created(id){
  
 }
    }
}
</script>
<style>
.navlist{
 width:414px;
 height:40px;
 border-bottom:1px solid rgba(151,151,151,0.1);
 position:relative;
 top:10px;
}
.navli{
 width:135px;
 height:40px;
 padding:10px 0px;
 text-align:center;
 float:left;
 margin:0 1.2rem;
 line-height:40px;
 background:#ddd;
}
.navli i{
 font-style: normal;
 font-size: 16px;
}
.activeT{
 color:#00ba6b;
 padding-bottom: .3rem;
 border-bottom: 2px solid #00ba6b;
}
.swiper_con{
 width:414px;
 margin-bottom:40px;
 position:relative;
 top:10px;
} 
.choosegrand{
 position:absolute;
 top:-3;
 right:0;
}
.show{
 display:block;
}
.none{
 display:none;
}
</style>
<style scoped>
    *{padding:0px;margin:0px;}
    .page-tabbar{
        overflow:hidden;
    }
    .page-wrap{
        overflow:auto;
        padding:0;
        top:0px;
        left:0px;
    }
    .page-wrap h1{
        font-size: 18px;
        margin-left:10px;
        padding-top:6px;
        color:#aaa;
    }
    .backTo{
       background-color:#cd1317;
       width:100%;
       height:50px;
    }
    .backTo span{
      display: inline-block;
      margin-top:12px;
      margin-left:10px;
      color:#fff;
      width:15px;
      height:30px;
      font-size: 2em;
    }
     .backTo h2{
       font-size: 20px;
       color:#fff;
       width:120px;
       height:27px;
       margin:auto;
       margin-top:-30px;
    }
    .backTo img{
       color:#fff;
       width:35px;
       height:40px;
       position:absolute;
       right:20px;
       top:5px;
    }
    .span{
        width:398PX;
        height:23px;
    }
     .span p{
       margin-top:10px;
       margin-left:10px;
    }
    .span h2{
      font-size: 16px;
      color:#f00;
      margin-left:60px;
      margin-top:-18px;
    }
    .span h6{
       font-size: 12px;
       color:#aaa;
       margin-left:130px;
       margin-top:-15px;
    }
    .ul{
        width:404px;
        height:62px;
        margin-top:60px;
        margin-left:10px;
    }
    .ul li{
        width:99px;
        height:44px;
        padding-left:5px;
        border:1px solid #ddd;
        float:left;
        line-height: 40px;
        text-indent: 25px;
    }
    .ul li:hover{
        color:#fff;
        background:#000;
    }
    .size{
         width:398px;
         
         margin-left:10px;
    }
    .size P{
        margin-left:10PX;
        margin-bottom:10px;
    }
    .size span{
        width:26px;
        height:31px;
        border:1px solid #ddd;
        padding:0px 8px 0px 0px ;
        margin:4px 8px;
    }
    .size h4{
        font-size: 14px;
        margin-left:10px;
        margin-top:20px;
    }
    .size button{
        width:47px;
        height:37px;
        background:#ddd;
        margin-left:0px;
        margin-top:15px;
    }
    .size input{
        width:60px;
        height:37px;
        background:#fff;
        margin-top:15px;
    }
    .bt{
        margin-top:10px;
        margin-left:10px;
    }
    .bt .bt1{
        margin-top:5px;
        width:157px;
        height:37px;
        background:#5EB95E;
        color:#fff;
    }
    .bt .bt1:hover{
        background:rgb(33, 176, 212);
        color:#000;
    }
    .bt .bt2{
        margin-top:5px;
        width:157px;
        height:37px;
        background:#DD514c;
        color:#fff;
        margin-left:20px;
    }
    .map{
        width:414px;
        height:82px;
        margin-top:10px;
    }
    .map p{
        margin-left:10px;
        margin-top:10px;
    }
    .map img{
        width:30px;
        height:35px;
        margin-left:-12px;
        margin-top:-10px;
    }
    .map h5{
         width:80px;
         height:35px;
        margin-left:260px;
        margin-top:-32px;
        color:#095F8A;
    }
   .adress{
       position:relative;
       width:400px;
       height:40px;
       border:1px solid #ddd;
   }
    .adress img{
        width:25px;
        height: 35px;
        top:0px;
        position:absolute;
    }
    .adress li{
     float:left;
     padding-left:60px;
     margin-top:6px;
     
    }
    .adress li>p{
     float:left;
     margin-left:30px;
     font-size: 18px;
    }
</style>
