<template>
  <div class="hello">
    <div v-if="show" class="box"></div>
    {{ show }}
    <div @click="isShow">显示</div>
    <div @click="isHide">隐藏</div>
  </div>
</template>

<script>

// function useShow() {
//       let show = ref(true);
//      const isHide = () => (show.value = false)
//      const isShow = () => (show.value = true)
//     return {show,isHide,isShow}
//   }
import { ref,onMounted } from "vue";
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
      isShow()
    })
    console.log("setup",props,context);
    // 单独的方法使用
   let show = ref(true)
   function isShow() {show.value = !show.value}
   function isHide() {show.value = false}
   return {show,isShow,isHide}
    // 封装法使用
    // const {show,isHide,isShow} = useShow()
    //return { show, isShow, isHide };


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
