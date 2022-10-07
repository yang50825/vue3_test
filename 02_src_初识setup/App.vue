<template>
  <h1>一个人的信息</h1>
  <h2>姓名{{ name }}</h2>
  <h2>年龄{{ age }}</h2>
  <button @click="sayHello">说话</button>
</template>

<script>
import { h } from 'vue'
export default {
  name: 'App',
  //   此处只是测试一下setup
  setup() {
    // 数据
    let name = '张三'
    let age = 17
    // 方法
    function sayHello() {
      alert(`我叫${name}, 我今年${age}岁了， hello`)
    }

    // 返回一个对象（常用）
    // return {
    //   name,
    //   age,
    //   sayHello,
    // }

    // 返回一个函数（渲染函数）
    // return () => {
    //   return h('h1', 'hello')
    // }
  },
}
</script>

<style></style>
