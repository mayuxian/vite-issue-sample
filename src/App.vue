<template>
  <img alt="Vue logo" src="./assets/logo.png" />
  <!-- <HelloWorld msg="Hello Vue 3 + Vite" /> -->
  <div
    id="teleport"
    class="teleport"
    style="height: 100px; background: gray"
  ></div>
  <div  style="position: relative">
    <h3>Tooltips with Vue 3 Teleport</h3>
    <div>
      <modal-button></modal-button>
    </div>
  </div>
</template>

<script >
import { defineComponent } from 'vue'
import ModalButton from './components/ModalButton.vue'
// import HelloWorld from './components/HelloWorld.vue'
export default defineComponent({
  components: {
    ModalButton,
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
