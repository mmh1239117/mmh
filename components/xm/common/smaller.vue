<template>
    <div>
        <div class="slider-stager">
            <ul ref='sli' class="sliders">
                <li>
                    <img src="../../../assets/bing-2.jpg" alt="">
                </li>
                <li>
                    <img src="../../../assets/bing-3.jpg" alt="">
                </li>
                <li>
                    <img src="../../../assets/bing-4.jpg" alt="">
                </li>
                <li>
                    <img src="../../../assets/bing-5.jpg" alt="">
                </li>
                <li>
                    <img src="../../../assets/bing-2.jpg" alt="">
                </li>
            </ul>
        </div>
    </div>
</template>
 
<script>
    export default {
        name: "slider",
        data() {
            return {
                index: 1,
            }
        },
        created() {
            this.autoLoops()
 
        },
        methods: {
            autoLoops() {
                setInterval(()=>{
                    this.$refs.sli.style.left = -414*this.index + 'px'
                    this.$refs.sli.style.transition= "all 0.5s"
                    this.index++
                    if(parseInt(this.$refs.sli.style.left) <= -600){
                        setTimeout(()=>{
                            //这个setTimeout是因为left=-600px，transition有0.5s执行动画，需要等它执行完成后，再设置left=0，
                            //否则，直接跳到left=0,动画生硬，
                            this.$refs.sli.style.left = 0 + 'px'
                            this.$refs.sli.style.transition= "all 0s"
                            this.index = 1
                        },500)
                    }
                },3000)
 
            }
        }
    }
</script>
 
<style>
    li {
        list-style: none;
    }
    input, img {
        border: none;
    }
</style>
<style>
    .slider-stager {
        width: 100%;
        height: 233px;
        border: 0.1px grey solid;
        margin:1px auto;
        position: relative;
        overflow: hidden;
        top:0;
        margin-top:-50px;
    }
    .sliders {
        position: absolute;
        width: 500%;
        height: 100px;
        left: 0px;
        top: 0;
    }
    .sliders li {
        list-style: none;
        float: left;
    }
    .sliders img {
        width: 414px;
        height: 233px;
    }
  
</style>
