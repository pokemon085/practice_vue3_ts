<template>
  <div class="app">
    hello
    <p>{{ name }}-{{ age }}</p>
    <button @click="changeName('aaa')">change name</button>
    <button @click="changeAge(30)">change age</button>
  </div>
</template>

<script lang="ts">
import { defineComponent, reactive, toRefs, ref } from "vue";

export default defineComponent({
  name: "App",
  components: {},
  // setup() {
  //   // const state = reactive({
  //   //   name:'Link',
  //   //   age:25 as string |number
  //   // })
  //   // //toRefs (会影响到原始数据)會將原本 響應式物件 轉為 普通響應式物件。其中在toRefs後的物件與值 是引用關係 且 每個值都轉為 ref 來達到 內部值 保有響應性。
  //   // return {...toRefs(state)}

  //   //ref函数将某个对象中的属性变成响应式数据，修改响应式数据是不会影响到原始数据。
  //   const name = ref("Link");
  //   const age = ref<string | number>(25);
  //   age.value = 50;
  //   return { name, age };
  // },
  data() {
  return {
    name: "Link",
    age: 22 as number | string,
  };
  },
  methods: {
    changeName(name: string) {
      this.name = name;
      return name;
    },
    changeAge(age: string | number) {
      this.age = age;
      return age;
    },
  },
});
</script>

<style>
</style>
