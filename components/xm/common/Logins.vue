<template>
<div class="container">
  <div class="tipslogin">
    <span>你需要登录才能继续访问</span>
    <span class="closeSpan">关闭</span>
  </div>
  <div class="imgDiv">
    <img src="../../../assets/img1.jpg" class="logo" alt="">
  </div>
  <div class="operateDiv">
     <!-- 01账户 -->
    <mt-field :placeholder="accountPlaceholder" v-model="uname" class="myinput"></mt-field>
     <!-- 02密码 -->
    <mt-field v-show="isUserAccount" :palceholder="defaultAccountText" type="password" v-model="upass" class="myinput"></mt-field>
  </div>
  <div>
    <mt-button type="primary" size="large" @click="changeLoginMethod">
      {{defaultAccountText}}
    </mt-button>
  <!-- 03短信验证 -->
    <mt-button size="large" class="mybutton" @click="login">登录</mt-button>
  </div>
  <!-- 04免费注册 -->
  <!-- 05登录和切换登陆方式 -->
</div>
</template>
<script>
export default {
    data(){
       return {
         accountPlaceholder:"手机号/邮箱/会员名",
         uname:"",
         upass:"",
         defaultAccountText:"账号密码登录",
         isUserAccount:true
       }
    },
    created() {
       
    },
    methods: {
      login(){
        /*if(!this.uanme){
          this.$messagebox("","请输入用户名")
        }else if(!this.upass){
          this.$messagebox("","请输入密码")
        }*/
         var n=this.uname;
            var p=this.upass;
            // 2.获取用户输入密码 3-8
            // 3.创建2个正则表达式
            var nreg=/^\w{3,10}$/;
            var preg=/^\w{3,8}$/;
            // 4.判断用户名格式不正确 提示出错
            if(!nreg.test(n)){
                this.$toast("用户名格式不正确");
                return;
            }
            if(!preg.test(n)){
                this.$toast("密码格式不正确");
                return;
            }
            // 6.将用户名和密码发送 ajax请求
            var url="login";
            var obj={uname:n,upass:p};
            // 7.并且获取服务器返回结果
            this.axios.get(url,{params:obj}).then(result=>{
              if(result.data.code==1){
                // 跳转指定的组件
                this.$router.push("/Index");
              } else{
                this.$messagebox("消息",result.data.msg);
              }
              
            });
      },
      changeLoginMethod(){
        if(this.isUserAccount){
          this.accountPlaceholder="请输入手机号码";
          this.defaultAccountText="短信密码验证"
        }else{
          this.accountPlaceholder="账户密码登录";
          this.defaultAccountText="手机/邮箱/用户名";
        }
        this.isUserAccount=!this.isUserAccount;
      }
    }
}
</script>
<style scoped>
   *{padding:0;margin:0;}
    /* 你需要登录才能继续仿问的布局样式 */
    .tipslogin {
      display: flex;
      justify-content: space-between;
      align-items: center;
      height: 52px;
      background: #494949;
      padding-left: 20px;
      padding-right: 20px;
    }
    /* 半闭样式 */
    .closeSpan {
      color: rgb(153, 153, 153)
    }
    /* 图片 logo 根样式 */
    .imgDiv {
      display: flex;
      justify-content: center;
    }
    /* 图片样式 */
    .logo{
      margin-top:15px;
      width: 100px;
      height: 100px;
      border-radius:10px
    }
    /* 上面的线隐藏 */
    .mint-cell-wrapper  {
      background-image: linear-gradient(180deg, #fff, #fff 0%, transparent 0%);
    }
   /* 输入框底边框样式 */
    .mint-cell-wrapper  {
      border-bottom: 1px solid #ff5000;
    }

    /* 修改按钮按钮下的默认颜色 */
    .mint-button::after {
      background-color: transparent;
    }
    /* 操作区域的样式*/
    .operateDiv {
      padding-left: 20px;
      padding-right: 20px;
    }
    /* 输入框边距 */
    .myinput {
     background:rgb(238, 238, 238);
      margin-top: 10px;
    }
    /* 获取短信验证码字体颜色 */
    .getCode {
      color:#ff5000;
      font-size: 17px;
      border-left:1px solid #b5b5b5;
      padding-left: 7px;
    }
    /* 免费注册根样式 */
    .registerDiv {
      margin-top: 30px;
      display: flex;
      justify-content: space-between;
      align-items: center;
    }
    /* 免费注册字体样式*/
    .registerDiv span {
      color: #555;
    }
    /* 登录短信验证按钮边距 */
    .mybutton {
      margin-top: 30px;
    }
    /* 修改默认 butoon 的样式 达到和淘宝登录一样 */
    .mint-button--default {
      background: -webkit-linear-gradient(left,#ff9000,#ff5000) no-repeat;
      border-radius: 25px;
      color: #fff;
      width:90%;
      margin-left:20px;
      height: 48px;
      margin-top:20px;
    }
    /* 同上 */
    .mint-button--primary {
      border-radius: 25px;
      height: 48px;
      width:90%;
      margin-left:20px;
      background-color: transparent;
      border: 1px solid #ff5000;
      color: #ff5000;
      margin-top:20px;
    }
    /* 修改默认弹框的样式，达到基本和淘宝的效果一样 */
    .mint-msgbox{
      border-radius: 8px;
      width: 70%;
    }
    /* 弹出框内容样式 */
    .mint-msgbox-content {
      min-height: 50px;
      font-size: 18px;
    }
    /* 弹出内容居中 */
    .mint-msgbox-message{
      line-height: 50px;
    }
    /* 弹出框确定按钮样式 */
    .mint-msgbox-btns{
      height: 60px;
    }
    /* 弹出框确定按钮字体 */
    .mint-msgbox-confirm {
      color: #f40;
    }
</style>