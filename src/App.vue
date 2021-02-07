<template>
  <img alt="Vue logo" src="./assets/logo.png" />

  <div>
    <h2>reactive的issue</h2>
    <TestReactive></TestReactive>
  </div>
  <div v-if="false">
    <!-- 指定到此处,正常显示 -->
    <div>teleport的issue</div>
    <div
      id="teleport"
      class="teleport"
      style="height: 100px; background: gray"
    ></div>
    <!-- issue:若指定teleport的锚点到modal-button(内部使用teleport)的父级节点,
  则会报以下错,这个是否属于错误,是否会完善修复吗?
  runtime-dom.esm-bundler.js:30 Uncaught (in promise) TypeError: Cannot read property 'parentNode' of null
  at parentNode (runtime-dom.esm-bundler.js:30) -->
    <div style="position: relative">
      <!-- <div style="position: relative"> -->
      <h3>Tooltips with Vue 3 Teleport</h3>
      <div>
        <modal-button></modal-button>
      </div>
    </div>
  </div>
</template>

<script >
import { defineComponent } from 'vue'
import ModalButton from './components/ModalButton.vue'
import TestReactive from './components/TestReactive.vue'
// import HelloWorld from './components/HelloWorld.vue'
export default defineComponent({
  components: {
    ModalButton,
    TestReactive,
  },
})
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
