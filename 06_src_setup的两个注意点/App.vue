<template>
  <Demo msg="hello" name="张三" @hello="showHelloMsg">
    <template v-slot:qwe>
      <span>hello</span>
    </template>
    <template v-slot:asd>
      <span>world</span>
    </template>
  </Demo>
</template>

<script>
import Demo from './components/Demo'
export default {
  name: 'App',
  components: {
    Demo,
  },
  setup() {
    function showHelloMsg(value) {
      alert(`hello, ${value}`)
    }

    return {
      showHelloMsg,
    }
  },
}
</script>

<style></style>
