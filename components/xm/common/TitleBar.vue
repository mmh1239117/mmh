<template>
    <div class="page-head">
        <!-- 顶部标题子组件
        weixin/common/TitleBar.vue -->
        <span>{{leftTitle}}</span>
        <div class="right-head">
            <div class="searchdiv" @click="search">  
                <router-link  :to="{path:'/Logins'}" ><img :src="rightFirstImg" style="width:30px;height:30px;margin-left:-335px;" /></router-link>
            </div>
            <div class="searchdiv" style="margin-left:20px;" @click="add">
                <img :src="rightSecondImg" style="width:30px;height:30px;margin-left:15px;"/>
            </div>
        </div>
    </div>
</template>

<script>

export default { 
    props:{
        leftTitle:{default:""},
        rightFirstImg:{default:""},
        rightSecondImg:{default:""},
        search:{type:Function},
        add:{type:Function},
    },
    data(){
        return{
            
        }
    },
    methods:{
      
    }
}
</script>

<style>
    .page-head{
        display:flex;
        position:fixed;
        z-index:999;
        width:100%;
        justify-content:space-between;
        align-items:center;
        background-color:#f00;
        padding-right:7px;
        padding-left:7px;
        height:48px;
        color:#fff;
        font-size:18px;

    }
    .page-head span{
        margin:auto;
        transform: translateX(30px);
    }
    .right-head{
        display:flex;
        align-items:center;
        line-height:10px;
    }
    .searchdiv img{
        background:rgba(0,0,0,0.1);
        margin-right:10px;
    }
</style>
