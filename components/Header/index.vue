<template>
  <div>
    <div id="navbar">
      <div style="width:80%;margin: 0 auto">
        <Bird style="float:left;margin-right:10px"/>
        <div style="float:left;font-size:30px;" class="masked">&lt;/&gt;leeruigan</div>
        <div id="navbar-right">
          <a-popover title="换肤">
            <template slot="content">
              <p>
                R：
                <a-slider
                  @change="e => {handleChange("red", e)}"
                  :min="0"
                  :max="255"
                  :defaultValue="165"
                />
              </p>
              <p>
                G：
                <a-slider
                  @change="e => {handleChange("green", e)}"
                  :min="0"
                  :max="255"
                  :defaultValue="135"
                />
              </p>
              <p>
                B：
                <a-slider
                  @change="e => {handleChange("blue", e)}"
                  :min="0"
                  :max="255"
                  :defaultValue="255"
                />
              </p>
            </template>
            <div class="border-box">
              <a-button icon="smile" type="dashed">换肤</a-button>
            </div>
          </a-popover>
        </div>
      </div>
    </div>
  </div>
</template>
<script>
import Bird from "@/components/Bird";
export default {
  components: {
    Bird
  },
  mounted() {},
  methods: {
    handleChange(name, value) {
      const eleBody = document.querySelector("body");
      eleBody.style.setProperty("--" + name, value);
    }
  }
};
</script>
<style>
#navbar {
  overflow: hidden;
  background-color: rgb(248, 248, 248);
  padding: 10px;
  transition: 0.4s;
  position: fixed;
  width: 100%;
  top: 0;
  z-index: 99;
}

#navbar a {
  float: left;
  color: black;
  text-align: center;
  padding: 12px;
  text-decoration: none;
  font-size: 18px;
  line-height: 25px;
  border-radius: 4px;
}

#navbar #logo {
  font-size: 35px;
  font-weight: bold;
  transition: 0.4s;
}

#navbar a:hover {
  background-color: #ddd;
  color: black;
}

#navbar a.active {
  background-color: dodgerblue;
  color: white;
}
#navbar-right {
  float: right;
}

:root {
  /* 定义RGB变量 */
  --red: 165;
  --green: 135;
  --blue: 255;
  /* 文字颜色变色的临界值，建议0.5~0.6 */
  --threshold: 0.5;
  /* 深色边框出现的临界值，范围0~1，推荐0.8+*/
  --border-threshold: 0.8;
}

.btn {
  font-size: 150%;
  padding: 0.5em 2em;
}
body {
  /* 按钮背景色就是基本背景色 */
  background: rgb(var(--red), var(--green), var(--blue));

  /** 
   * 使用sRGB Luma方法计算灰度（可以看成亮度）
   * 算法为：
   * lightness = (red * 0.2126 + green * 0.7152 + blue * 0.0722) / 255
  */
  --r: calc(var(--red) * 0.2126);
  --g: calc(var(--green) * 0.7152);
  --b: calc(var(--blue) * 0.0722);
  --sum: calc(var(--r) + var(--g) + var(--b));

  --lightness: calc(var(--sum) / 255);

  /**
   * --lightness近似看成亮度，范围0~1，此时，和临界值--threshold做比较：
   * 大于，则正数，和-999999%相乘，会得到一个巨大负数，浏览器会按照合法边界0%渲染，也就是亮度为0，于是颜色是黑色；
   * 小于，则和-999999%相乘，会得到一个巨大的正数，以最大合法值100%渲染，于是颜色是白色；
  */
  color: hsl(0, 0%, calc((var(--lightness) - var(--threshold)) * -999999%));

  /**
   * 确定边框透明度。
   * 如果亮度比--border-threshold值大，在说明按钮背景色比较淡，我们出现一个深色边框；
   * 如果亮度比较小，说明按钮背景色较深，没有必要出现边框。
     此时，--border-alpha计算后为负值，透明度小于0的时候，浏览器会按照0渲染，因此，边框透明。
  */
  --border-alpha: calc((var(--lightness) - var(--border-threshold)) * 100);
  /* 设置边框相关样式 */
  border: 0.2em solid;
  border-color: rgba(
    calc(var(--red) - 50),
    calc(var(--green) - 50),
    calc(var(--blue) - 50),
    var(--border-alpha)
  );
}

.border-box {
  display: inline-block;
  padding: 10px;
  position: relative;
}
.border-box::before {
  content: "";
  position: absolute;
  left: 0;
  top: 0;
  right: 0;
  bottom: 0;
  border: 2px solid #cd0000;
  animation: borderAround 1.5s infinite linear;
}
@keyframes borderAround {
  0%,
  100% {
    clip: rect(0 148px 10px 0);
  }
  /* 25% { clip: rect(0 148px 116px 146px); } */
  50% {
    clip: rect(90px 148px 116px 0);
  }
  /* 75% { clip: rect(0 2px 116px 0); } */
}
/* CSS3 text-fill-color + animation文字渐变光波流动动画 */
@media all and (-webkit-min-device-pixel-ratio: 0) and (min-resolution: 0.001dpcm) {
  .masked {
    background-image: -webkit-linear-gradient(
      left,
      #147b96,
      #e6d205 25%,
      #147b96 50%,
      #e6d205 75%,
      #147b96
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