<template>
  <h1>一个人的信息</h1>
  <h2 v-if="person.name">姓名{{ person.name }}</h2>
  <h2>年龄{{ person.age }}</h2>
  <h2 v-if="person.sex">性别{{ person.sex }}</h2>
  <h3>工作种类 {{ person.job.type }}</h3>
  <h3>工作种类 {{ person.job.salary }}</h3>
  <h3>爱好：{{ person.hobby }}</h3>
  <button @click="changeInfo">修改人的信息</button>
  <button @click="addSex">添加一个sex属性</button>
  <button @click="deleteName">删除一个name属性</button>
</template>

<script>
import { ref, reactive } from 'vue'
export default {
  name: 'App',
  //   此处只是测试一下setup
  setup() {
    // 数据
    let person = reactive({
      name: '张三',
      age: 17,
      job: {
        type: '前端',
        salary: '30k',
      },
      hobby: ['抽烟', '喝酒', '烫头'],
      a: {
        b: {
          c: 666,
        },
      },
    })

    // 方法
    function changeInfo() {
      person.name = '李四'
      person.age = 18
      person.job.type = '后端'
      person.job.salary = '40k'
      person.hobby[0] = '学习'
    }

    function addSex() {
      person.sex = '男'
    }

    function deleteName() {
      delete person.name
    }

    // 返回一个对象（常用）
    return {
      person,
      changeInfo,
      addSex,
      deleteName,
    }

    // 返回一个函数（渲染函数）
    // return () => {
    //   return h('h1', 'hello')
    // }
  },
}
</script>

<style></style>
