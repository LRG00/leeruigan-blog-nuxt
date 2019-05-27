<template>
  <a-locale-provider :locale="zh_CN">
    <section class="container">
      <div class="main">
        <div class="gutter-container">
          <a-row type="flex" :gutter="16">
            <a-col class="gutter-row gutter-left" style="width: 176px">
              <div class="gutter-box">
                <Nav/>
              </div>
            </a-col>
            <a-col class="gutter-row gutter-center" style="width: 660px">
              <div class="gutter-box">
                <MyList/>
              </div>
            </a-col>
            <a-col class="gutter-right" style="width: 290px">
              <div class="gutter-box">
                <div class="input-search">
                  <a-input-search
                    placeholder="请输入关键字"
                    @search="onSearch"
                  />
                </div>
                <div class="calendar">
                  <a-calendar :fullscreen="false"/>
                </div>
                <div class="ysfm-wrap">
                  <strong>向</strong>
                  <strong>我</strong>
                  <strong>的</strong>
                  <strong>衣</strong>
                  <strong>食</strong>
                  <strong>父</strong>
                  <strong>母</strong>
                  <strong>鞠</strong>
                  <strong>躬</strong>
                </div>
                <div class="tag-wrap">
                  <ul>
                    <li><a-icon type="crown" /> 诗和远方 [22]</li>
                    <li><a-icon type="crown" /> 计算机 [46]</li>
                    <li><a-icon type="crown" /> node.js [9]</li>
                    <li><a-icon type="crown" /> php [22]</li>
                    <li><a-icon type="crown" /> react.js [46]</li>
                    <li><a-icon type="crown" /> 前端 [9]</li>
                    <li><a-icon type="crown" /> vue [22]</li>
                    <li><a-icon type="crown" /> 算法 [46]</li>
                    <li><a-icon type="crown" /> nuxt.js [9]</li>
                    <li><a-icon type="crown" /> 后端 [22]</li>
                    <li><a-icon type="crown" /> 摄影 [46]</li>
                    <li><a-icon type="crown" /> ios [9]</li>
                  </ul>
                </div>
              </div>
            </a-col>
          </a-row>
        </div>
      </div>
    </section>
  </a-locale-provider>
</template>

<script>
import MyList from "../components/List/index";
import Nav from "../components/Nav";
import zh_CN from "ant-design-vue/lib/locale-provider/zh_CN";
import moment from "moment";
import "moment/locale/zh-cn";

moment.locale("zh-cn");
export default {
  data() {
    return {
      zh_CN
    };
  },
  components: {
    MyList,
    Nav
  },
  mounted() {},
  methods: {
    onSearch () {

    }
  }
};
</script>

<style>
@media screen and (max-width: 1000px) {
  /* .gutter-left,.gutter-right {
    float: none;
  } */
}
.gutter-container {
  margin-top: 90px;
}
.main {
  width: 60%;
  min-width: 1140px;
  margin: 0 auto;
}
.gutter-center {
  background: #f8f8f8;
}
.ysfm-wrap {
  background: #f8f8f8;
  padding: 5px;
  margin-top: 10px;
  text-align: center;
}
.tag-wrap {
  background: #f8f8f8;
  margin-top: 10px;
  padding:  10px;
}
.tag-wrap ul {
  padding: 0;
  margin: 0;
}
.tag-wrap ul > li {
  height: 30px;
  line-height: 30px;
  color: #7d7d7d;
  display: inline-block;
  background: #dfdfdf;
  margin: 5px;
  padding: 0 5px;
}
.tag-wrap ul > li:hover {
  background: #888;
  cursor: pointer;
} 
.calendar {
  background: #f8f8f8;
}
.input-search {
  margin-bottom: 10px;
}
.input-search .ant-input {
  background: #f8f8f8;
}
</style>