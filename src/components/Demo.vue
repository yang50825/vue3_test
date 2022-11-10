<template>
  <h2>当前求和是：{{ sum }}</h2>
  <button @click="sum++">点我++</button>
  <hr />
  <h2>姓名：{{ name }}</h2>
  <h2>年龄：{{ age }}</h2>
  <h2>薪资：{{ job.j1.salary }}K</h2>
  <h2 v-if="person.car">座驾信息：{{ person.car }}</h2>
  <button @click="name += '~'">修改姓名</button>
  <button @click="age++">增长年龄</button>
  <button @click="job.j1.salary++">涨薪</button>
  <button @click="showRawPerson">输出最原始的person</button>
  <button @click="addCar">给人添加一台车</button>
  <button @click="person.car.name += '!'">换车名</button>
  <button @click="person.car.price++">换价格</button>
</template>

<script>
import { ref, reactive, toRefs, toRaw, markRaw } from 'vue'
export default {
  name: 'Demo',
  setup() {
    // 数据
    let person = reactive({
      name: '张三',
      age: 18,
      job: {
        j1: {
          salary: 20,
        },
      },
    })

    let sum = ref(0)

    function addCar() {
      let car = {
        name: 'Benzi',
        price: 40,
      }
      person.car = markRaw(car)
    }

    function showRawPerson() {
      // 将一个由reactive生成的响应式对象转为普通对象
      const p = toRaw(person)
      console.log(p)
    }

    return {
      person,
      ...toRefs(person),
      showRawPerson,
      addCar,
      sum,
    }
  },
}
</script>
