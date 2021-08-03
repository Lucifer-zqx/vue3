<template>
  <div>
    <h1>一个人的信息</h1>
    <!-- 模板直接使用属性名获取 -->
    <h2>姓名：{{ person.name }}</h2>
    <h2>年龄：{{ person.age }}</h2>
    <button @click="person.age++">点我++</button>

    <hr />

    <h2>品牌:{{ person.car.brand }}</h2>
    <h2>价格:{{ person.car.price }}w</h2>
    <button @click="person.car.price++">点我改价</button>
  </div>
</template>

<script>
import { reactive } from "vue";
export default {
  name: "App",
  setup() {
    //通过reactive使基本数据变成响应式

    //reactive不能操作基本数据类型
    // const name = reactive('张三')
    // const age = reactive(18)
    const person = reactive({
      name:'zhangsan',
      age:18,
      car: { brand: "Audi", price: 40 },
    });
    //观察reactive生成的数据
    //reactive生成的是Proxy代理对象Proxy
    console.log(person)
    //返回值代表向外提供的数据和方法
    return {
      person
    };
  },
};
</script>

<style>
</style>
