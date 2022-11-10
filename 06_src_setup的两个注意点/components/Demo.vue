<template>
  <h1>一个人的信息</h1>
  <h2>姓名: {{ person.name }}</h2>
  <h2>年龄: {{ person.age }}</h2>
  <button @click="test">hello</button>
  <slot name="qwe"></slot>
</template>

<script>
import { ref, reactive } from 'vue'
export default {
  name: 'Demo',
  props: ['msg', 'name'],
  emits: ['hello'],
  beforeCreate() {
    console.log('---beforeCreate---')
  },
  //   此处只是测试一下setup
  setup(props, context) {
    console.log('---setup---', context.slots)
    // 数据
    let person = reactive({
      name: '张三',
      age: 17,
    })

    function test() {
      // context.emit('自定义事件名', 参数)
      context.emit('hello', person.name)
    }
    // 返回一个对象（常用）
    return {
      person,
      test,
    }

    // 返回一个函数（渲染函数）
    // return () => {
    //   return h('h1', 'hello')
    // }
  },
}
</script>

<style></style>
