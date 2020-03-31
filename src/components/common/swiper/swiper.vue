<template>
    <div class="swiper">
        <ul id="swiper_contair" @mousedown="mousedown" @mouseenter="mouseEnter" @mouseleave="mouseLeave">
        <li class="swiper_item"><img src="../../../assets/img/swiper/01_750x390.jpg"></li>
        <li class="swiper_item"><img src="../../../assets/img/swiper/02_750x390.jpg"></li>
        <li class="swiper_item"><img src="../../../assets/img/swiper/03_750x390.jpg"></li>
        <li class="swiper_item"><img src="../../../assets/img/swiper/04_750x390.jpg"></li>
        <li class="swiper_item"><img src="../../../assets/img/swiper/01_750x390.jpg"></li>
        </ul>
    </div>
</template>

<script>
  export default {
    name: "swiper",
    data(){
      return{
        timer:null,
        intervalTime:3000,
        flag:0, //记录偏移量
        left:0,
      }
    },
    computed:{
      swiper_cntair(){
         return document.getElementById('swiper_contair');
       }
    },
    methods:{
      mouseEnter(){
        //鼠标进入，清除定时器
        console.log('清除定时器');
        // this.swiper_cntair.setAttribute('style','transition:none')
        if (this.timer != null){
          clearInterval(this.timer);
          this.timer = null;
        }
      },
      mouseLeave(){
        //重启定时器
        console.log('重启定时器');
        this.timer = this.runtimer();

      },
      mousedown(){
        // // console.log(this.swiper_cntair.style.left);
        // let disx = e.pageX - this.swiper_cntair.offsetLeft;
        // document.onmousemove = function (e) {
        //   let dv = e.pageX - disx;
        //   // this.swiper_cntair.style.left = e.pageX - disx +'px';
        //   this.swiper_cntair.setAttribute('style','left:'+dv+'px');
        // }
        // document.onmouseup = function () {
        //   document.onmousemove = document.onmouseup = null;
        // }
      },
      runtimer(){
        //方法返回定时器标识
         return setInterval(() =>{
             this.swiper_cntair.setAttribute('style','left:'+this.flag+'px');
             if(this.flag > -1700)
             {
                 this.flag -= 340;
             }
             else {
               //在翻到最后一页的时候，消除动画，直接跳到第一页
               this.swiper_cntair.setAttribute('style','transition:none')
               this.flag = 0
             }
           },this.intervalTime);
      }
    },
    mounted(){
      //第一次加载时，启动定时器
      this.timer = this.runtimer();
    }
  }

</script>

<style scoped>
    *,
    ul,
    li,
    body{
        margin: 0;
        padding: 0;
    }
    ul,li{
        list-style: none;

    }
    img{
        display: block;
        width: auto;
        height: auto;
        max-height: 100%;
        max-width: 100%;
        pointer-events: none;
}
    .swiper{
        display: inline-block;
        text-align: left;
        width: 340px;
        height: 180px;
        position: relative;
        overflow: hidden;
    }
    #swiper_contair{
        /*每张图片340px宽*/
        position: absolute;
        width: 1700px;
        /*翻页的动画*/
        transition: left 0.5s;
        /*left: -340px;*/
    }
    .swiper_item{
        height: 180px;
        width: 340px;
        display: inline-block;
        background-color:honeydew;
        overflow: hidden;

    }
</style>