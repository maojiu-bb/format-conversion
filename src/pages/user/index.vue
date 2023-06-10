<template>
  <view class="user">
    <view class="top-img">
      <image class="img" src="" mode="scaleToFill" />
    </view>
    <view class="info">
      <view class="avatar">
        <image class="img" src="@/static/logo.png" mode="scaleToFill" />
      </view>
      <view class="name">未登录</view>
    </view>
    <view class="func">
      <view
        class="func-item"
        v-for="item in funcItems"
        :key="item.id"
        @click="funcitemHandle(item.id)"
      >
        <image class="left-icon" :src="item.leftIcon" mode="scaleToFill" />
        <text>{{ item.text }}</text>
        <image class="right-icon" :src="item.rightIcon" mode="scaleToFill" />
      </view>
    </view>
  </view>
</template>

<script setup lang="ts">
import { ref } from 'vue'

type Titem = {
  id: number
  text: string
  leftIcon: string
  rightIcon: string
}

const funcItems = ref<Titem[]>([
  {
    id: 1,
    text: '作者',
    leftIcon: '/static/images/author.png',
    rightIcon: '/static/images/right.png'
  },
  {
    id: 2,
    text: '关于',
    leftIcon: '/static/images/about.png',
    rightIcon: '/static/images/right.png'
  },
  {
    id: 3,
    text: '退出',
    leftIcon: '/static/images/tuichu.png',
    rightIcon: '/static/images/right.png'
  }
])

const funcitemHandle = (id: number) => {
  if (id === 1) {
    uni.navigateTo({
      url: '../author/index'
    })
  }
}
</script>

<style scoped lang="scss">
@import '@/styles/user.scss';
</style>
