<template>
  <view class="home">
    <view class="title">
      <text>快捷文档格式转换</text>
      <view>支持多种格式</view>
    </view>
    <view class="main">
      <view
        class="item"
        v-for="item in itemData"
        :key="item.id"
        @click="choose(item.id)"
      >
        <image class="img" :src="item.cover" mode="scaleToFill" />
        <view class="info">{{ item.text }}</view>
      </view>
    </view>
    <Tip v-model:text="tipMessage" v-show="isShowTip"></Tip>
  </view>
</template>

<script setup lang="ts">
import { ref } from 'vue'
import Tip from '@/components/tip/index.vue'

type Titem = {
  id: number
  cover: string
  text: string
}

type TextArray = {
  ext: string
  url: string
}

const itemData = ref<Titem[]>([
  {
    id: 1,
    cover: '/static/images/png.png',
    text: 'PNG 转 PDF'
  },
  {
    id: 2,
    cover: '/static/images/docx.png',
    text: 'DOCX 转 PDF'
  },
  {
    id: 3,
    cover: '/static/images/pdf.png',
    text: 'PDF 转 TXT'
  },
  {
    id: 4,
    cover: '/static/images/md.png',
    text: 'MD 转 PDF'
  },
  {
    id: 5,
    cover: '/static/images/pdf.png',
    text: 'PDF 转 PNG'
  },
  {
    id: 6,
    cover: '/static/images/jpg.png',
    text: 'JPG 转 PDF'
  },
  {
    id: 7,
    cover: '/static/images/pdf.png',
    text: 'PDF 转 DOCX'
  },
  {
    id: 8,
    cover: '/static/images/txt.png',
    text: 'TXT 转 PDF'
  },
  {
    id: 9,
    cover: '/static/images/docx.png',
    text: 'DOCX 转 PNG'
  }
])

const extArray = ref<TextArray[]>([
  { ext: 'png', url: 'http://localhost:3006/api/pngToPdf' },
  { ext: 'docx', url: 'http://localhost:3006/api/docxToPdf' },
  { ext: 'pdf', url: 'http://localhost:3006/api/pdfToTxt' },
  { ext: 'md', url: 'http://localhost:3006/api/mdToPdf' },
  { ext: 'pdf', url: 'http://localhost:3006/api/pdfToPng' },
  { ext: 'jpg', url: 'http://localhost:3006/api/jpgToPdf' },
  { ext: 'pdf', url: '' },
  { ext: 'txt', url: 'http://localhost:3006/api/txtToPdf' },
  { ext: 'docx', url: 'http://localhost:3006/api/docxToPng' }
])

const tipMessage = ref<string>('')
const isShowTip = ref<boolean>(false)

const choose = (id: number) => {
  extArray.value.forEach((item: TextArray, index: number) => {
    if (index + 1 === id) {
      uploadFile(item.ext, item.url)
    }
  })
}

const uploadFile = (extension: string, url: string) => {
  uni.chooseMessageFile({
    count: 1,
    type: 'file',
    extension: [extension],
    success: (res) => {
      const file = res.tempFiles[0]
      uni.uploadFile({
        url: url,
        filePath: file.path,
        name: 'file',
        success: (res) => {
          const result = JSON.parse(res.data)
          if (result.code === 200) {
            isShowTip.value = true
            tipMessage.value = '文件转换成功！'
            setTimeout(() => {
              isShowTip.value = false
            }, 1500)
          } else {
          }
        },
        fail: (_err) => {
          isShowTip.value = true
          tipMessage.value = '文件上传失败！'
          setTimeout(() => {
            isShowTip.value = false
          }, 1500)
        }
      })
    },
    fail: (err) => {
      console.log('选择文件失败！', err)
    }
  })
}
</script>

<style scoped lang="scss">
@import '@/styles/home.scss';
</style>
