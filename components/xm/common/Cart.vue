<template>
<div class="headers">
  <div class="form">
    <input type="text" v-model="text"/>
    <button v-on:click="tabs">提交评论</button>
  </div>
 
 <div class="text">
   <div v-for="(name,index) in arr" v-on:click="dele(index)" :key="index"><span class="span">{{name.text}}</span></div> 
 </div>
 <ul class="ly">
     <!-- <p>@15856565</p>
     <span>这个人好帅啊,为什么这么帅</span>
     <p>@s56ds5as</p>
     <span>这个人好帅啊,这么帅</span> -->
     <li><img src="../../../assets/img1.jpg" alt="">
     <input class="input" type="text" placeholder="昵称（他的用户名）          2017-8.12"><hr>那，那是一封写给南部母亲的信。我茫然站在骑楼下，我又看到永远的樱子走到街心。
     </li>
     <li><img src="../../../assets/img1.jpg" alt="">
     <input class="input1" type="text" placeholder="昵称（他的用户名）           2019-6.12"><hr>其实雨下得并不大，却是一生一世中最大的一场雨。而那封信是这样写的，年轻的樱子知不知道呢？</li>
 </ul>
</div>
</template>
<script>
export default {
data(){
  return {
   text:"",
   arr:[]
  }
},
 methods: {
    tabs:function(){
       this.arr.push({text:this.text});
       this.text="";
       console.log(this.arr)
    },
    dele:function(index){
      this.arr.splice(index,1)
     }
 }
};
</script>

<style >
    *{margin:0;padding:0;}
    .headers{
        margin-top:10px;
        padding-bottom:5px;
    }
    .form:first-child input{
        width:100%;
        height:120px;
        background:#eee;
    }
    .form:nth-child(1) button{
        left:0px;
        background:#fff;
    }
    .form:nth-child(1) button:hover{
        background:greenyellow;
    }
   .ly {
        margin-top:50px;
        width:100%;
        height:260px;
        background:#ddd;
    }
    .ly img{
      width:50px;
      height:50px;
      margin-top:30px;
      border-radius: 50%;
      margin-left:10px;
    }
    .ly .input{
      width:80%;
      position:absolute;
      margin-left:12px;
      bottom:170px;
      justify-content: space-between;
    }
    .ly .input1{
      width:80%;
      position:absolute;
      margin-left:12px;
      bottom:45px;
    }
    .text .span{
      position: absolute;
      width:100%;
      margin-top:5px;
      line-height:35px;
      padding-left:10px;
      height:40px;
      background:greenyellow;
    }
</style>