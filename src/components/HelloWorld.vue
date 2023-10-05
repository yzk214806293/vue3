<template>
  <div class="hello">
    <!-- <div v-if="show" class="box"></div>
    {{ show }}
    <div @click="isShow">显示</div>
    <div @click="isHide">隐藏</div> -->


    <!-- <div>{{ num }}</div>
    <button @click="addNum">加1</button> -->
    {{ arrs }}
    <div @click="editr">更改</div>
    <input type="text" v-model="inpur">
  </div>
</template>

<script>

// function useShow() {
//       let show = ref(true);
//      const isHide = () => (show.value = false)
//      const isShow = () => (show.value = true)
//     return {show,isHide,isShow}
//   }
import {   ref,onMounted } from "vue";
export default {
  name: 'HelloWorld',
  // props: {
  //   msg: String
  // },
  beforeCreate() {
    console.log("1 beforeCreate");
  },
  created(){
    console.log("2created");
  },
  beforeMount(){
    console.log("3beforeMount");
  },
  mounted(){

    console.log("4mounted");
  },
  beforeUpdate(){
    console.log("5 beforeUpdate");
  },
  updated(){
    console.log("6updated");
  },
  beforeUnmount(){
    console.log("7 beforeUnmount");
  },
  unmounted(){
    console.log("8 unmounted");
  },
  setup(props, context) {
    // ① 第1个参数为props。props为一个对象，内部包含了父组件传递过来的所有prop数据
    // ② 第2个参数为一个对象context。context对象包含了attrs，slots， emit属性，
    // ③ 如果在data()中也定义了同名的数据，则以setup()中为准。

    // 注 setup 优先级最高 最先执行的 然后上面正常执行顺序  例如同级的 mounted 优先执行 setup里面的onMounted 然后在执行mounted
    onMounted(() => {
      console.log('Component is mounted!')
      // onart()
    })
    console.log("setup",props,context);
    // 单独的方法使用
  //  let show = ref(true)
  //  function isShow() {show.value = !show.value}
  //  function isHide() {show.value = false}
  //  return {show,isShow,isHide}
    // 封装法使用
    // const {show,isHide,isShow} = useShow()
    //return { show, isShow, isHide };

    // 不使用ref函数(这个不是响应式的 num有变化 但是dom上的num是不变的 因为不是响应式)
    // let num=1
    // function addNum(){
    //   num++
    //   console.log(num)
    // }
    // return {num,addNum}

    //使用ref函数 响应式的
    // let num=ref(1),
    //   addNum=()=>{
    //       num.value++
    //       console.log(num);
    //   }
    //   return {num,addNum}

    //复杂数据类型 响应式

    let arrs=ref([])
    let inpur = ref('')
    const arr = [{name:'小明',age:12},{name:'小刚',age:13}]
      function onart(){
          arr.forEach(element => {
            arrs.value.push({...element,sex:'男'})
          });
      }
   onart()
   function editr() {
    arrs.value[0].name ='哈哈哈'
    inpur.value = '2222'
    // console.log(arrs.value[0].name ='哈哈哈')

  }
   return {arrs,arr,editr,inpur}
  },
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
.box{
  width: 200px;
  height: 200px;
  background: pink;
}
</style>
