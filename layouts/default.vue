<template>
  <div>
    <header id="header">
      <MyHeader/>
    </header>
    <section id="main">
      <nuxt/>
    </section>
    <footer id="foot">
      <MyFooter/>
    </footer>
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
    let reallyDocumentTitle;
    document.addEventListener(
      "visibilitychange",
      function(event) {
        if (event.target.hidden || event.target.webkitHidden) {
          reallyDocumentTitle = document.title;
          document.title = "长路漫漫，唯剑作伴 死亡如风，常伴吾身！长路漫漫，唯剑作伴 死亡如风，常伴吾身！";
        } else {
          document.title = reallyDocumentTitle;
        }
      },
      false
    );
    this.fnTextPopup([
      "点哪呢",
      "你再点",
      "你还敢点？",
      "你再点试试？",
      // "富强",
      // "民主",
      // "文明",
      // "和谐",
      // "自由",
      // "平等",
      // "公正",
      // "法治",
      // "敬业",
      // "诚信",
      // "友善",
      // "平等",
      // "爱国"
    ]);
  },
  methods: {
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

/* 点击出现字 自强 */
@media all and (-webkit-min-device-pixel-ratio: 0) and (min-resolution: 0.001dpcm) {
  .text-popup {
    background-image: -webkit-linear-gradient(
      left,
      red,
      blue 25%,
      red 50%,
      blue 75%,
      red
    );
    -webkit-text-fill-color: transparent;
    background-clip: text;
    background-size: 200% 100%;
    animation: textPopup 4s infinite linear;
  }
}
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
#main {
  margin-bottom: 20px;
}
</style>
