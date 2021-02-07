<template>
  <div>
    <h3>
    Issue description: Using ES6 class to instantiate objects, after reactive, only click "classState Add", data no response
    </h3>
    <button @click="onClassAdd">classState Add</button>

    <div>testValue:{{ testValue }}</div>
    <div>classState.testValue值:{{ classState.testValue }}</div>
    <br />
    <br />
    <button @click="onAdd">state Add</button>
    <div>value:{{ value }}</div>
    <div>state.value:{{ state.value }}</div>
  </div>
</template>

<script lang="ts">
import { defineComponent, reactive, toRefs } from 'vue'
//This emulates a library written in ES6 Class
class TestProxy {
  _testValue: number = 0
  constructor() {
    this._testValue = 0
  }
  get testValue() {
    return this._testValue
  }
  set testValue(val) {
    this._testValue = val
  }
  add() {
    this._testValue++
  }
}
export default defineComponent({
  setup() {
    console.log('setup');
    
    const _obj = new TestProxy()
    const classState = reactive(_obj)
    const state = reactive({
      value: 0,
    })
    function onClassAdd() {
      _obj.add()
      // _obj.testValue++
    }
    function onAdd() {
      state.value++
    }
    return {
      ...toRefs(classState),
      ...toRefs(state),
      classState,
      state,
      onClassAdd,
      onAdd,
    }
  },
})
</script>

<style scoped>
</style>