<template>
  <footer id="footer" class="footer">
    <div class="container">
      <div class="footer-content">

        <!-- chinese -->
        <span>
          <span>由&nbsp;</span>
          <nuxt-link to="/project">NodePress</nuxt-link>
          <span>、</span>
          <nuxt-link to="/project">Nuxt.js</nuxt-link>
          <span>&nbsp;和&nbsp;日月星辰&nbsp;强力驱动&nbsp;</span>
          <span>&nbsp;&nbsp;|&nbsp;&nbsp;</span>
          <nuxt-link to="/about">长路漫漫，唯剑作伴</nuxt-link>
          <span>&nbsp;死亡如风，常伴吾身</span>
        </span>
      </div>
    </div>
  </footer>
</template>

<script>
  export default {
    name: 'pc-footer',
  }
</script>

<style>
  footer {
    margin-top: 1em;
    background-color: #f8f8f8;

  }
    footer .container {
      position: relative;

    }
          footer .container .footer-content {
        padding: 1em;
        font-size: .9em;
        text-align: center;
        text-transform: uppercase;
      }
</style>