<template>
  <div>
    <h1>一个人的信息</h1>
    <h2>姓名：{{ name }}</h2>
    <h2>年龄：{{ age }}</h2>
    <h2>性别：{{ sex }}</h2>
    <h2>a的值是：{{ a }}</h2>
    <button @click="sayHello">说话(Vue3所配置的——sayHello)</button>
    <br />
    <br />
    <button @click="sayWelcome">说话(Vue2所配置的——sayWelcome)</button>
    <br />
    <br />
    <button @click="test1">
      测试一下在Vue2的配置中去读取Vue3中的数据、方法
    </button>
    <br />
    <br />
    <button @click="test2">
      测试一下在Vue3的setup配置中去读取Vue2中的数据、方法
    </button>
  </div>
</template>

<script>
export default {
  name: "App",
  //vue2的数据写法
  data(){
    return {
      sex:'male',
      a1:100
    }
  },
  //vue2的方法写法
  methods:{
    sayWelcome(){
      alert('欢迎你')
    },
    test1(){
      //读取2中的数据
     console.log(this.sex)
     console.log(this.a)
     //读取3中的数据(可行)
     console.log(this.name)
     console.log(this.age)
     
    }
  },

  //此处无响应式
  setup() {
    //vue3数据
    let name = '张三'
    let age = 18
    // let a = 200
    //vue3的方法
    function sayHello(){
      alert(`我叫${name}，我${age}岁了，你好啊！`)
    }

    //setup函数中的this为undefined
    console.log(this)

    function test2(){
      //读取3中的数据
      console.log(name)
      console.log(age)
      console.log(sayHello)
      console.log('##########################')

      //函数中的this为对外提供数据和方法的对象的代理对象
      console.log(this)
      //读取2中的数据（不可行）
      console.log(this.sex)
    }
    //返回值代表向外提供的数据和方法
    return{
      name,
      age,
      // a,
      sayHello,
      test2
    }
  },
};
</script>

<style>
</style>
