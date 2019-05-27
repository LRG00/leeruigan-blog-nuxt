<template>
  <div>
    <div id="my-header">
      <div class="header-main">
        <Bird style="float:left;padding-top:10px"/>
        <div style="float:left;font-size:20px" class="masked">长路漫漫，唯剑作伴</div>
        <div id="my-header-right">
          <Drawer/>
        </div>
      </div>
    </div>
  </div>
</template>
<script>
import Bird from "@/components/Bird";
import Drawer from "@/components/Drawer";
export default {
  components: {
    Bird,
    Drawer
  },
  mounted() {
    window.onscroll = () => {
      this.scrollFunction();
    };
  },
  methods: {
    scrollFunction() {
      if (
        document.body.scrollTop > 80 ||
        document.documentElement.scrollTop > 80
      ) {
        document.getElementById("my-header").style.padding = "10px";
        document.getElementById("my-header").style.opacity = "0.8";
      } else {
        document.getElementById("my-header").style.padding = "10px";
        document.getElementById("my-header").style.opacity = "1";
      }
    }
  }
};
</script>
<style>
#my-header {
  /* overflow: hidden; */
  height: 80px;
  background-color: rgb(248, 248, 248);
  transition: 0.4s;
  position: fixed;
  width: 100%;
  top: 0;
  z-index: 99;
}
.header-main {
  width: 80%;
  height: 100%;
  line-height: 80px;
  /* 水平居中 */
  position: absolute;
  left: 50%;
  transform: translate(-50%);
  /* border: 1px solid red; */
}
#my-header-right {
  float: right;
}

/* CSS3 text-fill-color + animation文字渐变光波流动动画 */
@media all and (-webkit-min-device-pixel-ratio: 0) and (min-resolution: 0.001dpcm) {
  .masked {
    background-image: -webkit-linear-gradient(
      left,
      pink,
      #e6d205 25%,
      pink 50%,
      #e6d205 75%,
      pink
    );
    -webkit-text-fill-color: transparent;
    background-clip: text;
    background-size: 200% 100%;
    animation: masked-animation 4s infinite linear;
  }
}
@keyframes masked-animation {
  0% {
    background-position: 0 0;
  }
  100% {
    background-position: -100% 0;
  }
}
</style>