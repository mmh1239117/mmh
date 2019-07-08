<template>
    <div class="container">
        <div class="good-item" v-for="(item,index) of list" :key="index">
            <router-link  :to="{path:'/productSmall'}" ><img :src="require('../../../assets/img2.jpg')"/></router-link>
            <h4>{{item.title}}</h4>
            <div class="info">
                <span class="now">￥{{item.price}}</span>
                <h5>佣金<br>2.84</h5>
                <h6>积分<br>12</h6>
            </div>
            <div class="imgs">
            <a href="javascript:;"><img :src="require('../../../assets/icon1.png')" alt=""></a>
            <a href="javascript:;"><img :src="require('../../../assets/icon2.png')" alt=""></a>
            <a href="javascript:;"><img :src="require('../../../assets/icon3.png')" alt=""></a>
            </div>
        </div>
        <mt-button size="large" type="primary" @click="loadMore">加载更多</mt-button>
    </div>
</template>

<script>
export default {
    data(){
        return{
            list:[],
            pno:0,
            pageSize:4
        }
    },
    created(){
        this.loadMore();
    },
    methods:{
        loadMore(){
            //获取当前页码加1
            this.pno++;
            //创建一个url地址
            var url="product";
            //创建一个参数
            var obj={pno:this.pno,pageSize:this.pageSize};
            //发送ajax
            this.axios.get(url,{params:obj}).then(result=>{
               var rows=this.list.concat(result.data.data);
            //  console.log(result);
               this.list=rows;
            })
            //接收服务器返回数据
            //保存list
            //console.log("123");
        }
    }
}
</script>
<style scoped>  /*scoped*/
    /* 最外层父元素 */
    .container{
        display:flex;/*弹性布局*/
        flex-wrap:wrap;/*子元素换行*/
        justify-content:space-between;
        padding:4px;
    }
    .container .good-item{
        width:49%;/*元素宽度*/
        border:1px solid #ccc;
        margin:2px 0;
        padding:2px;
        display:flex;/*弹性布局*/
        flex-direction:column;/*方向按列*/
        min-height:247px;
        border-radius:5px;
    }
    .good-item img{
        width:171px;
        height:200px;
        margin:0 auto;
        margin-left:9px;
    }
    .good-item h4{
        font-size:16px;
        text-indent:10px;
        font-weight: bold;
    }
    .info .now{
      color:#EA1010;
      font-size:16px; 
    }
     .info{
        position:relative;
        margin-bottom:10px;
    }
    .container .info h5{
        position:absolute;
        top:-10px;
        left:90px;
        font-size:13px;     
    }
    .container .info h6{
        position:absolute;
        top:-10px;
        right:30px;
        font-size:13px;
        
    }
    .imgs{
      float:left;  
    }
    .imgs img{
      width:20px;
      height:18px;
      margin-left:35px;
    }
</style>
