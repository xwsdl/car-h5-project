<template>
  <van-tabbar v-model="active" @change="onChange">
    <van-tabbar-item name="home" icon="wap-home">首页</van-tabbar-item>
    <van-tabbar-item name="records" icon="records">标签</van-tabbar-item>
    <van-tabbar-item name="setting" icon="setting">标签</van-tabbar-item>
    <van-tabbar-item name="cart" icon="cart">购物车</van-tabbar-item>
    <van-tabbar-item name="user" icon="user">个人中心</van-tabbar-item>
  </van-tabbar>
</template>

<script setup>
import { ref } from 'vue'

const active = ref('home')
const onChange = (name) => {
  console.log('当前选中标签:', name)
  // 可以在这里添加路由跳转或其他逻辑
  if(true){
    
  }
}
</script>

<style>
</style>