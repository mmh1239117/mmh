<template>
    <div class="page-tabbar">
        <div class="page-wrap">
            <!-- 01:自定义标题子组件 -->
            <titlebar
            leftTitle="营养生活"
            :rightFirstImg="require('../../assets/ic_friends_circle.png')"
            :rightSecondImg="require('../../assets/ic_add.png')"
            :search="mysearch"
            :add="myadd"
            ></titlebar>
            <!-- 02:48px占位符 -->
            <div style="margin-top:48px;"></div>
            <!-- 轮播子组件 -->
            <awesome ></awesome>
            <!--导航栏 -->
            <!-- 聊天 -->
            <div class="nav">
            <img src="../../assets/img1.jpg" alt="">
            <div>
             <ul>
               <li>关于我们</li>
               <li>新闻中心</li>
              <li><router-link style="color:#fff;"  :to="{path:'/trolley'}" >购物车</router-link></li>
             </ul>
           </div>
        </div>
         <!-- 正文 -->       
            <!-- 03:切换的面板 -->
            <mt-tab-container v-model="selected" class="page-tabbar-container">
                <mt-tab-container-item id="product">
                    <product></product>
                </mt-tab-container-item>
                <mt-tab-container-item id="cart">
                    <cart></cart>
                </mt-tab-container-item>
                <mt-tab-container-item id="me">
                    <msg></msg>
                </mt-tab-container-item>
            </mt-tab-container>
            <!-- 04:底部导航栏 -->
            <mt-tabbar v-model="selected" fixed>
                <mt-tab-item id="product">
                    商品
                </mt-tab-item>
                <mt-tab-item id="cart">
                    客服
                </mt-tab-item>
                <mt-tab-item id="me">
                    我的分享
                </mt-tab-item>
            </mt-tabbar>
        </div>
    </div>
</template>

<script>
import TitleBar from "./common/TitleBar"
import awesome from "./common/awesome.vue"
import product from "./common/product.vue"
import trolley from "./common/trolley.vue"
import Cart from "./common/Cart.vue"
import Msg from "./common/Msg.vue"
export default {
    data(){
        return{
        selected:"product",
        }
    },
    components:{
        "titlebar":TitleBar,
        "awesome":awesome,
        "product":product,
        "tralley":trolley,
        "cart":Cart,
        "msg":Msg
        },
    methods:{
        mysearch(){
            console.log(1);
        },
        myadd(){
            console.log(2);
        }
    }
}
</script>

<style>
    .nav{
      width:100%;
      background:#333333 no-repeat;
      height:30rpx;
      cursor:pointer;
    }
    .nav img{
      margin-left:30px;
      width:55px;
      height:55px;
      border-radius:50%;
      padding:3px;
      background-color:#fff;
    }
    .nav ul{
        display:flex;
        margin-left:100px;
       cursor: pointer;
       transition:all 2s;
    }
    .nav ul li{
        padding:0px;
        margin-top:-40px;
        margin-left:40px;
        color:#fff;
       background-color: #333333; 
    }
    .nav ul li:hover{
      color:#fff;
    }
</style>
<style scoped>
    *{padding:0px;margin:px;}
    .page-tabbar{
        overflow:hidden;
    }
    .page-wrap{
        overflow:auto;
        padding:0;
    }
</style>
