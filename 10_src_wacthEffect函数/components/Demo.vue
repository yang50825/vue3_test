<template>
  <h2>当前求和为：{{ sum }}</h2>
  <button @click="sum++">点我+1</button>
  <hr />
  <h2>当前的信息为：{{ msg }}</h2>
  <button @click="msg += '!'">修改msg</button>
  <hr />
  <h2>姓名： {{ person.name }}</h2>
  <h2>年龄：{{ person.age }}</h2>
  <h2>薪资：{{ person.job.j1.salary }}</h2>
  <button @click="person.name += '~'">修改姓名</button>
  <button @click="person.age++">年龄+1</button>
  <button @click="person.job.j1.salary++">涨薪</button>
</template>

<script>
import { ref, watch, reactive, watchEffect } from 'vue'
export default {
  name: 'Demo',
  setup() {
    let sum = ref(0)
    let msg = ref('hello')
    let person = reactive({
      name: '张三',
      age: 17,
      job: {
        j1: {
          salary: 10,
        },
        j2: {
          salary: 20,
        },
      },
    })

    watchEffect(() => {
      const x1 = sum.value
      const x2 = person.job.j1.salary
      console.log('watchEffect所指向的回调执行了')
    })

    return {
      sum,
      msg,
      person,
    }
  },
}
</script>

<style></style>
