<template>
  <view class="user">
    <view class="top-img">
      <image
        class="img"
        src="https://tse1-mm.cn.bing.net/th/id/OIP-C.ZfafvLeoky7XsCHXM5Ll9AHaDe?w=350&h=164&c=7&r=0&o=5&dpr=1.3&pid=1.7"
        mode="scaleToFill"
        @click="previewBackImage"
      />
    </view>
    <view class="info">
      <view class="avatar">
        <image
          class="img"
          src="@/static/images/avatar.jpg"
          mode="scaleToFill"
        />
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
    <view class="about" v-show="isShowAbout">
      <view class="version">Version1.0.0</view>
      <view class="close" @click="closeAbout">x</view>
    </view>
    <view class="logout" v-show="isShowLogout">
      <view class="title">确定退出吗？</view>
      <view class="button">
        <button @click="cancelLogout">取消</button>
        <button @click="confirmLogout">确认</button>
      </view>
    </view>
    <Tip v-show="isShowTip" v-model:text="tipMessage"></Tip>
  </view>
</template>

<script setup lang="ts">
import { ref } from 'vue'
import Tip from '@/components/tip/index.vue'

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
    text: '文件',
    leftIcon: '/static/images/file.png',
    rightIcon: '/static/images/right.png'
  },
  {
    id: 3,
    text: '关于',
    leftIcon: '/static/images/about.png',
    rightIcon: '/static/images/right.png'
  },
  {
    id: 4,
    text: '退出',
    leftIcon: '/static/images/tuichu.png',
    rightIcon: '/static/images/right.png'
  }
])

const isShowAbout = ref<boolean>(false)
const isShowLogout = ref<boolean>(false)

const isShowTip = ref<boolean>(false)
const tipMessage = ref<string>('')

const funcitemHandle = (id: number) => {
  switch (id) {
    case 1:
      uni.navigateTo({
        url: '../author/index'
      })
      break
    case 2:
      uni.navigateTo({
        url: '../fileList/index'
      })
      break
    case 3:
      isShowAbout.value = true
      break
    case 4:
      isShowLogout.value = true
      break
  }
}

const cancelLogout = () => {
  isShowLogout.value = false
}
const confirmLogout = () => {
  console.log('confirm')
}

const closeAbout = () => {
  isShowAbout.value = false
}

const previewBackImage = () => {
  uni.previewMedia({
    sources: [
      {
        type: 'image',
        url: 'https://tse1-mm.cn.bing.net/th/id/OIP-C.ZfafvLeoky7XsCHXM5Ll9AHaDe?w=350&h=164&c=7&r=0&o=5&dpr=1.3&pid=1.7'
      }
    ],
    success: (res) => {
      console.log('图片预览成功！', res)
    },
    fail: (_err) => {
      isShowTip.value = true
      tipMessage.value = '图片预览失败！'
    }
  })
}
</script>

<style scoped lang="scss">
@import '@/styles/user.scss';
</style>
