<template>
  <view class="home">
    <view class="title">
      <text>快捷文档格式转换</text>
      <view>支持多种格式</view>
    </view>
    <view class="main">
      <view class="item">
        <image class="img" src="@/static/logo.png" mode="scaleToFill" />
        <view class="info">PDF 转 txt</view>
      </view>
      <view class="item">
        <image class="img" src="@/static/logo.png" mode="scaleToFill" />
        <view class="info">PDF 转 txt</view>
      </view>
      <view class="item">
        <image class="img" src="@/static/logo.png" mode="scaleToFill" />
        <view class="info">PDF 转 txt</view>
      </view>
      <view class="item">
        <image class="img" src="@/static/logo.png" mode="scaleToFill" />
        <view class="info">PDF 转 txt</view>
      </view>
      <view class="item">
        <image class="img" src="@/static/logo.png" mode="scaleToFill" />
        <view class="info">PDF 转 txt</view>
      </view>
      <view class="item">
        <image class="img" src="@/static/logo.png" mode="scaleToFill" />
        <view class="info">PDF 转 txt</view>
      </view>
      <view class="item">
        <image class="img" src="@/static/logo.png" mode="scaleToFill" />
        <view class="info">PDF 转 txt</view>
      </view>
      <view class="item">
        <image class="img" src="@/static/logo.png" mode="scaleToFill" />
        <view class="info">PDF 转 txt</view>
      </view>
      <view class="item">
        <image class="img" src="@/static/logo.png" mode="scaleToFill" />
        <view class="info">PDF 转 txt</view>
      </view>
    </view>
  </view>
</template>

<script setup lang="ts"></script>

<style scoped lang="scss">
.home {
  .title {
    text-align: center;
    margin-top: 60px;
    font-size: 18px;
    line-height: 1.6;
  }
  .main {
    margin: 100px auto;
    margin-top: 60px;
    width: 380px;
    height: 450px;
    display: flex;
    flex-wrap: wrap;
    .item {
      width: 120px;
      height: 140px;
      background-color: #f0f0f0;
      margin-right: 10px;
      border-radius: 10px;
      &:nth-child(3n) {
        margin-right: 0;
      }
      .img {
        width: 80px;
        height: 80px;
        margin-left: 20px;
        margin-top: 10px;
      }
      .info {
        text-align: center;
        margin-top: 10px;
      }
    }
  }
}
</style>
