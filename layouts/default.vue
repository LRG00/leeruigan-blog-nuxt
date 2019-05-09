<template>
  <div>
    <MyHeader/>
    <nuxt/>
    <MyFooter/>
    <div @mouseenter="share" id="components-back-top-demo-custom">
      <a-back-top>
        <div class="ant-back-top-inner">顶部</div>
      </a-back-top>
    </div>
  </div>
</template>
<script>
import MyHeader from "../components/Header/index";
import MyFooter from "../components/Footer/index";
export default {
  components: {
    MyFooter,
    MyHeader
  },
  mounted() {
    this.fnTextPopup([
      "长路漫漫,唯剑作伴",
      "死亡如风,常伴吾身",
      "断剑重铸之日，骑士归来之时",
      "改变，就是好事",
      "人，终有一死，而有些人则需要一点小小的帮助",
      "黎明就在眼前",
      "要永远相信你的灵魂",
      "我用双手成就你的梦想",
      "我渴望有价值的对手",
      "时间，不在于你拥有多少，而在于你，怎样使用",
      "犯我德邦者，虽远必诛",
      "无形之刃，最为致命"
    ]);

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
        document.getElementById("navbar").style.padding = "10px";
        document.getElementById("navbar").style.opacity = "0.8";
      } else {
        document.getElementById("navbar").style.padding = "10px";
        document.getElementById("navbar").style.opacity = "1";
      }
    },
    share () {
      console.log('x')
    },
    fnTextPopup(arr, options) {
      // arr参数是必须的
      if (!arr || !arr.length) {
        return;
      }
      // 主逻辑
      var index = 0;
      document.documentElement.addEventListener("click", function(event) {
        var x = event.pageX,
          y = event.pageY;
        var eleText = document.createElement("span");
        eleText.className = "text-popup";
        this.appendChild(eleText);
        if (arr[index]) {
          eleText.innerHTML = arr[index];
        } else {
          index = 0;
          eleText.innerHTML = arr[0];
        }
        // 动画结束后删除自己
        eleText.addEventListener("animationend", function() {
          eleText.parentNode.removeChild(eleText);
        });
        // 位置
        eleText.style.left = x - eleText.clientWidth / 2 + "px";
        eleText.style.top = y - eleText.clientHeight + "px";
        // index递增
        index++;
      });
    }
  }
};
</script>
<style>
html {
  font-family: "Source Sans Pro", -apple-system, BlinkMacSystemFont, "Segoe UI",
    Roboto, "Helvetica Neue", Arial, sans-serif;
  font-size: 16px;
  word-spacing: 1px;
  -ms-text-size-adjust: 100%;
  -webkit-text-size-adjust: 100%;
  -moz-osx-font-smoothing: grayscale;
  -webkit-font-smoothing: antialiased;
  box-sizing: border-box;
}

*,
*:before,
*:after {
  box-sizing: border-box;
  margin: 0;
}

.button--green {
  display: inline-block;
  border-radius: 4px;
  border: 1px solid #3b8070;
  color: #3b8070;
  text-decoration: none;
  padding: 10px 30px;
}

.button--green:hover {
  color: #fff;
  background-color: #3b8070;
}

.button--grey {
  display: inline-block;
  border-radius: 4px;
  border: 1px solid #35495e;
  color: #35495e;
  text-decoration: none;
  padding: 10px 30px;
  margin-left: 15px;
}

.button--grey:hover {
  color: #fff;
  background-color: #35495e;
}

/* 点击出现字 自强 */
.text-popup {
  animation: textPopup 1s;
  color: red;
  user-select: none;
  white-space: nowrap;
  position: absolute;
  z-index: 99;
}
@keyframes textPopup {
  0%,
  100% {
    opacity: 0;
  }
  5% {
    opacity: 1;
  }
  100% {
    transform: translateY(-50px);
  }
}

  #components-back-top-demo-custom .ant-back-top {
    bottom: 100px;
  }
  #components-back-top-demo-custom .ant-back-top-inner {
    width: 64px; 
    line-height: 64px;
    text-align: center;
    background-color: #cd0000;
    color: #fff;
    border-radius: 50%;
  }
</style>
