<template>
  <div>
    <h1>一个人的信息</h1>
    <!-- 模板直接使用属性名获取 -->
    <h2>姓名：{{ name }}</h2>
    <h2>年龄：{{ age }}</h2>
    <button @click='age++'>点我++</button>

    <hr>

    <h2>品牌:{{car.brand}}</h2>
    <h2>价格:{{car.price}}w</h2>
    <button @click='car.price++'>点我改价</button>
  </div>
</template>

<script>
import {ref} from 'vue'
export default {
  name: "App",
  setup() {

    //通过ref使基本数据变成响应式
    const name = ref('张三')
    const age = ref(18)
    const car = ref({
      brand:'Audi',
      price:40
    })
    //JS代码操作ref生成的响应式数据，必须使用.value获取
    function sayHello(){
      alert(`我叫${name.value}，我${age.value}岁了，你好啊！`)
    }
    //观察ref生成的数据
    //ref生成的是一个ref实例对象refImpl,对于基本数据类型，值在value中，对于引用数据类型，是请求Proxy做的
    console.log(name)
    console.log(age)
    console.log(car)
    //返回值代表向外提供的数据和方法
    return{
      name,
      age,
      car,
      sayHello,
    }
  },
};
</script>

<style>
</style>
