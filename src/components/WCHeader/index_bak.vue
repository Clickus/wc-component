<template>
  <!-- <div class="header--wrapper">
    <div class="container">
      <img class="logo" src="../../assets/images/logo.png" alt="" />
      <h2>{{ title }}</h2>
    </div>
  </div> -->

  <div class="main">
    <button @click="setWhiteTheme">白色主题</button>
    <button @click="setBlackTheme">黑色主题</button>
    <div class="content">
      <div>Hello Vue3!</div>
    </div>
  </div>
</template>
<script lang="ts">
// 在模块作用域下执行 (仅一次)
export default {
  name: "WCHeader111",
  inheritAttrs: false, // 禁止父组件传递过来的属性 “透传” 到子组件的根节点
  customOptions: {
    name: "true",
  }, // 插件的自定义选项
};
</script>
<script lang="ts" setup>
import { reactive } from "vue";
defineProps({
  title: {
    type: String,
    default: "我的组件库",
  },
});

const theme: any = reactive({});
setWhiteTheme();
function setWhiteTheme() {
  theme.fontColor = "#000";
  theme.backgroundColor = "#fff";
}
function setBlackTheme() {
  theme.fontColor = "#fff";
  theme.backgroundColor = "#000";
}
</script>
<style scoped lang="less">
.content {
  color: v-bind("theme.fontColor");
  background-color: v-bind("theme.backgroundColor");
  height: @default-header-height;
}

.header--wrapper {
  position: fixed;
  height: @default-header-height;
  width: 100%;
  top: 0;
  left: 0;
  background-color: var(--wc-header);
  border-bottom: 1px solid #f1f1f1;
  z-index: 250;
  .container {
    height: 100%;
    margin: 0 auto;
    max-width: 1440px;
    display: flex;
    align-items: center;
    font-size: 16px;
    color: #333;
  }
  .logo {
    height: 50px;
  }
}
</style>
