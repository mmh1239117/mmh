<template>
    <div>
        <div class="msg">
            <img src="../../../assets/img1.jpg" alt="">
            <P>我是某某某 <br>我为某某某代言</P>
        </div>
        <div class="apple">
            <p>我的推广二维码</p>
            <img src="../../../assets/qrcode.jpg" alt="">
        </div>
        <div class="text">
            <p>我的推广代码</p>
            <textarea class="" rows="3" id="doc-ta-1">http://www.apple.com/abc?id=123456789</textarea>
        </div>
        <button class="btn">立即分享</button>
    </div>
</template>

<script>
export default {
    data(){
        return{}
    }
}
</script>

<style>
  *{margin:0;padding:0;}
  .msg{
      width:378px;
      height:100px;
      border:1px solid #ebe8e8;
      padding:15px;
      margin-left:15px;
      position:relative;
  }   
  .msg img{
      position:absolute;
      top:30px;
      left:60px;
      width:55px;
      height:55px;
      border-radius:50%;
  }   
  .msg p{
      font-size:21px;
      position:absolute;
      top:40px;
      left:145px;
      color:#333333;
  }   
  .apple{
      margin-top:20px;
      width:414px; 
      border-top:1px solid #ddd;
  }
  .apple p{
      font-size: 25px;
      margin-top:20px;
      color:#333333;
      text-align:center;
  }
  .apple img{
      width:150px;
      height:150px;
      border-radius:5px;
      margin-left:130px;
      margin-top:10px;
      padding:8px;
      border:1px solid #ddd;
  }   
  .text p{
    font-size: 16px;
    margin-left:10px;
    margin-top:15px;
  }
  .text #doc-ta-1{
      width:95%;
      height:80px;
    margin-left:10px;
    margin-top:5px;
  }
  .btn{
      background:#DD514C;
      width:95%;
      margin-left:10px;
      color:#fff;
      font-weight:bold;
  }
</style>