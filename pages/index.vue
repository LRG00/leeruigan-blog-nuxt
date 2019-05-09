<template>
  <section class="container">
    <div class="main">
      <div class="gutter-container">
        <a-row type="flex" :gutter="16">
          <a-col class="gutter-row gutter-left" style="width: 176px">
            <div class="gutter-box">
              <a-menu
                mode="inline"
                theme="dark"
                :defaultSelectedKeys="['1']"
              >
                <a-menu-item key="1">
                  <nuxt-link to="/life">明殿</nuxt-link>
                </a-menu-item>
                <a-menu-item key="2">宁静寺</a-menu-item>
                <a-menu-item key="3">琼宝阁</a-menu-item>
                <a-menu-item key="4">无色庵</a-menu-item>
                <a-menu-item key="5">天涯</a-menu-item>
                <a-menu-item key="6">狂浪生</a-menu-item>
                <a-menu-item key="7">德道</a-menu-item>
                <a-menu-item key="8">百鸣苑</a-menu-item>
              </a-menu>
            </div>
          </a-col>
          <a-col class="gutter-row gutter-center" style="width: 660px">
            <div class="gutter-box">
              <MyList />
            </div>
          </a-col>
          <a-col class="gutter-row gutter-right" style="width: 290px">
            <div class="gutter-box" style="padding-top:10px">
              <div :style="{  border: '1px solid #d9d9d9', borderRadius: '4px'}">
                <a-calendar :fullscreen="false" @panelChange="onPanelChange" />
                <Bird />
              </div>
            </div>
          </a-col>
        </a-row>
      </div>
    </div>
  </section>
</template>

<script>
import MyList from '../components/List/index'
import Bird from '../components/Bird'
export default {
  components: {
    MyList,
    Bird
  },
  mounted() {
  },
  methods: {
    onPanelChange(value, mode) {
      console.log(value, mode);
    },
  }
};
</script>

<style>
* {
  box-sizing: border-box;
}

body {
  margin: 0;
  font-family: Arial, Helvetica, sans-serif;
}

@media screen and (max-width: 1000px) {
  /* .gutter-left,.gutter-right {
    float: none;
  } */
}
.gutter-box {
  background: #f8f8f8;
  
}
.gutter-container {
  margin-top: 90px;
}
.main {
  width:60%;
  min-width: 1140px;
  margin: 0 auto;
}
.gutter-center {
  background: #f8f8f8;
}
.gutter-right {
  /* background: pink; */
}
</style>