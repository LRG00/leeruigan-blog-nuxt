<template>
  <a-menu
    mode="inline"
    style="background:#f8f8f8"
    :defaultSelectedKeys="['1']"
  >
    <a-menu-item key="1">
      <nuxt-link to="/life"><a-icon type="radar-chart" /> 明殿</nuxt-link>
    </a-menu-item>
    <a-menu-item key="2"><a-icon type="customer-service" /> 宁静寺</a-menu-item>
    <a-menu-item key="3"><a-icon type="step-forward" /> 琼宝阁</a-menu-item>
    <a-menu-item key="4"><a-icon type="hourglass" /> 无色庵</a-menu-item>
    <a-menu-item key="5"><a-icon type="bell" /> 天涯</a-menu-item>
    <a-menu-item key="6"><a-icon type="coffee" /> 狂浪生</a-menu-item>
    <a-menu-item key="7"><a-icon type="fire" /> 德道</a-menu-item>
    <a-menu-item key="8"><a-icon type="crown" /> 百鸣苑</a-menu-item>
  </a-menu>
</template>
<style>
.ant-menu:not(.ant-menu-horizontal) .ant-menu-item-selected {
  color: red;
  background: #dfdfdf;
  position: relative;
}
.ant-menu:not(.ant-menu-horizontal) .ant-menu-item-selected::before {
  content: "";
  position: absolute;
  left: 0;
  top: 0;
  right: 0;
  bottom: 0;
  border: 2px solid #c3c3c3;
  animation: borderAround 3s infinite linear;
}
.ant-menu:not(.ant-menu-horizontal) .ant-menu-item-selected::after {
  display: none;
}


@keyframes borderAround {
  0%,
  100% {
    clip: rect(0 170px 40px 0);
  }
  25% { clip: rect(0 148px 116px 146px); }
  50% {
    clip: rect(90px 148px 116px 0);
  }
  75% { clip: rect(0 2px 116px 0); }
}
</style>