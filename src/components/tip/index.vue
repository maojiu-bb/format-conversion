<template>
  <view class="tip">
    <view>{{ props.text }}</view>
  </view>
</template>

<script setup lang="ts">
const props = defineProps<{
  text: string
}>()
</script>

<style scoped lang="scss">
.tip {
  position: absolute;
  top: 50%;
  left: 50%;
  transform: translate(-50%, -50%);
  padding: 0 20px;
  height: 65px;
  background-color: rgba($color: #000000, $alpha: 0.5);
  border-radius: 15px;
  color: #eee;
  text-align: center;
  line-height: 65px;
  font-size: 20px;
}
</style>
