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
      <view class="func-item" v-for="(item, index) in funcItems" :key="index">
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
  text: string
  leftIcon: string
  rightIcon: string
}

const funcItems = ref<Titem[]>([
  {
    text: '作者',
    leftIcon: '/static/images/author.png',
    rightIcon: '/static/images/right.png'
  },
  {
    text: '关于',
    leftIcon: '/static/images/about.png',
    rightIcon: '/static/images/right.png'
  },
  {
    text: '退出',
    leftIcon: '/static/images/tuichu.png',
    rightIcon: '/static/images/right.png'
  }
])
</script>

<style scoped lang="scss">
@import '@/styles/user.scss';
</style>
