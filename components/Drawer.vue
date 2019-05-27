<template>
  <div>
    <a-button icon="heart" type="dashed" @click="showDrawer">
      主题
    </a-button>
    <a-drawer
      title="主题设置"
      placement="right"
      :closable="false"
      @close="onClose"
      :visible="visible"
    >
      <p><Skin /></p>
      <p>主题设置1...</p>
      <p>主题设置1...</p>
    </a-drawer>
  </div>
</template>
<script>
import Skin from "@/components/Skin";
export default {
  components: {
    Skin
  },
  data() {
    return {
      visible: false,
    }
  },
  methods: {
    showDrawer() {
      this.visible = true
    },
    onClose() {
      this.visible = false
    },
  },
}
</script>
