<template>
  <h1>一个人的信息</h1>
  <h2>姓名{{ name }}</h2>
  <h2>年龄{{ age }}</h2>
  <h3>工作种类 {{ job.type }}</h3>
  <h3>工作种类 {{ job.salary }}</h3>
  <h3>爱好：{{ hobby }}</h3>
  <button @click="changeInfo">修改人的信息</button>
</template>

<script>
import { ref, reactive } from 'vue'
export default {
  name: 'App',
  //   此处只是测试一下setup
  setup() {
    // 数据
    let name = ref('张三')
    let age = ref(17)
    let job = reactive({
      type: '前端',
      salary: '30k',
    })
    let hobby = reactive(['抽烟', '喝酒', '烫头'])
    // 方法
    function changeInfo() {
      name.value = '李四'
      age.value = 18
      job.type = '后端'
      job.salary = '40k'
      hobby[0] = '学习'
    }

    // 返回一个对象（常用）
    return {
      name,
      age,
      job,
      hobby,
      changeInfo,
    }

    // 返回一个函数（渲染函数）
    // return () => {
    //   return h('h1', 'hello')
    // }
  },
}
</script>

<style></style>
