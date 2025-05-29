<template>
  <div class="home">
    <van-search class="home-search" v-model="value" placeholder="请输入搜索关键词" />
    <van-swipe class="home-swipe my-swipe" :autoplay="3000" indicator-color="white">
      <van-swipe-item>1</van-swipe-item>
      <van-swipe-item>2</van-swipe-item>
      <van-swipe-item>3</van-swipe-item>
      <van-swipe-item>4</van-swipe-item>
    </van-swipe>
  </div>
  <!-- 菜单 -->
  <div class="home-menu">
    <div class="home-menu__item">
      <div class="home-menu__icon">
        <img src="@/assets/images/ershouche.png" width="50" height="50" />
      </div>
      <div class="home-menu__name">二手车</div>
    </div>

    <div class="home-menu__item">
      <div class="home-menu__icon">
        <img src="@/assets/images/suv.png" width="50" height="50" />
      </div>
      <div class="home-menu__name">SUV</div>
    </div>

    <div class="home-menu__item">
      <div class="home-menu__icon">
        <img src="@/assets/images/huoche.png" width="50" height="50" />
      </div>
      <div class="home-menu__name">货车</div>
    </div>

    <div class="home-menu__item">
      <div class="home-menu__icon">
        <img src="@/assets/images/gerenche.png  " width="50" height="50" />
      </div>
      <div class="home-menu__name">新能源车</div>
    </div>
    <div class="home-menu__item">
      <div class="home-menu__icon">
        <img src="@/assets/images/xinnengyuan.png" width="50" height="50" />
      </div>
      <div class="home-menu__name">个人车源</div>
    </div>
  </div>

  <!-- 分类 -->
  <div class="home-brand">
    <div class="home-brand__item" v-for="(brand, index) in brandList" :key="index">
      <img :src="brand.icon" class="home-brand__icon" />
      <span class="home-brand__name">{{ brand.name }}</span>
    </div>
  </div>

  <!-- 商品列表 -->
  <div class="home-product">
    <van-card
      v-for="(item, index) in 5"
      price="12.5万"
      desc="2015年 13.20万公里"
      title="宝马 5系 2014款 528Li 领先型"
      :thumb="getFile('good.png')"
      origin-price="15.5万"
    />
  </div>
</template>

<script setup>
import { getFile } from '@/utils/index.js'
import { ref, onMounted } from 'vue'
const value = ref('')
const images = ref([
  'https://fastly.jsdelivr.net/npm/@vant/assets/apple-1.jpeg',
  'https://fastly.jsdelivr.net/npm/@vant/assets/apple-2.jpeg',
])

// 获取图片名称到路径的映射
const imageMap = {}
Object.keys(images).forEach((path) => {
  const name = path.split('/').pop().replace('.png', '')
  imageMap[name] = images[path] // 保存动态导入函数
})

const brandList = ref([
  {
    name: '大众',
    icon: getFile('dazhong.png'),
  },
  {
    name: '丰田',
    icon: getFile('fengtian.png'),
  },
  {
    name: '本田',
    icon: getFile('bentian.png'),
  },
  {
    name: '奥迪',
    icon: getFile('aodi.png'),
  },
  {
    name: '宝马',
    icon: getFile('baoma.png'),
  },
  {
    name: '奔驰',
    icon: getFile('benchi.png'),
  },
  {
    name: '比亚迪',
    icon: getFile('BYD.png'),
  },
  {
    name: '更多',
    icon: getFile('more.png'),
  },
])
</script>

<style lang="scss" scoped>
@mixin flex($justify: space-between, $align: center) {
  display: flex;
  justify-content: $justify;
  align-items: $align;
}
.home {
  &-swipe {
    width: 100%;
    margin-top: 8px;
    border-radius: 10px;
  }
  &-menu {
    margin-top: 8px;
    padding: 16px;
    background-color: #fff;
    border-radius: 16px;
    display: flex;
    justify-content: space-between;
    align-items: center;

    box-shadow: 0 2px 8px rgba(0, 0, 0, 0.1);
    &__item {
      display: flex;
      flex-direction: column;
      align-items: center;
    }

    &__icon {
      width: 40px;
      height: 40px;
      img {
        width: 100%;
        height: 100%;
      }
    }

    &__name {
      font-size: 14px;
      color: #333;
      text-align: center;
      margin-top: 4px;
    }
  }

  &-brand {
    margin-top: 10px;
    background-color: #fff;
    border-radius: 16px;
    padding: 16px;
    box-shadow: 0 2px 8px rgba(0, 0, 0, 0.1);
    @include flex();
    flex-wrap: wrap;
    &__item {
      width: 25%;
      @include flex(flex-start, center);
      flex-direction: column;
    }

    &__icon {
      width: 40px;
      height: 40px;
    }

    &__name {
      font-size: 14px;
      color: #333;
      text-align: center;
      margin-top: 4px;
    }
  }

  &-product {
    margin-top: 10px;
    border-radius: 16px;
    padding-bottom: 50px;
  }
}
.my-swipe .van-swipe-item {
  color: #fff;
  font-size: 20px;
  line-height: 150px;
  text-align: center;
  background-color: #39a9ed;
}
</style>