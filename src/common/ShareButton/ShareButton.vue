<template>
  <div class="share-button">
    <button @click="shareContent">Share PWA</button>
  </div>
</template>

<script setup lang="ts">
import { defineProps } from 'vue'

const { title, text, url } = defineProps({
  title: String,
  text: String,
  url: String
})

const shareContent = async () => {
  try {
    const shareData = {
      title,
      text,
      url
    }

    if (navigator.share) {
      await navigator.share(shareData)
      console.log('Контент успешно поделен.')
    } else {
      console.error('Web Share API не поддерживается в вашем браузере.')
    }
  } catch (error) {
    console.error('Ошибка при попытке поделиться контентом:', error)
  }
}
</script>

<style scoped>
@import '@/common/ShareButton/styles.module.scss';
</style>
