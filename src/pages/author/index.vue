<template>
  <view class="author">
    <image class="avatar" :src="authorData.avatar" />
    <view class="info">
      <view class="name">{{ authorData.name }}</view>
      <view>{{ authorData.content }}</view>
      <view>{{ authorData.description }}</view>
    </view>
  </view>
</template>

<script setup lang="ts">
import { ref } from 'vue'

type Tauthor = {
  name: string
  avatar: string
  content: string
  description: string
}

const authorData = ref<Tauthor>({
  name: 'Mao Jiu (猫九)',
  avatar: '/static/images/avatar.jpg',
  content: '在午夜时分相遇，寻找真实的自己',
  description: '一位编程爱好者，主要使用的语言为Javascript。'
})
</script>

<style scoped lang="scss">
@import '@/styles/author.scss';
</style>
