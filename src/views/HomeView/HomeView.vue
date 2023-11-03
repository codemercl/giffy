<template>
  <section class="app">
    <HeaderComponent>
    <template #logo>
      <component :is="LogoComponent" />
    </template>
    <template #menu>
      <ShareButton :title="contentTitle" :text="contentText" :url="contentUrl" />
      <component :is="SearchComponent"  />
    </template>
  </HeaderComponent>
  <ContentComponent />
  </section>
</template>

<script setup lang="ts">
import HeaderComponent from '@/components/HeaderComponent/HeaderComponent.vue'
import LogoComponent from '@/components/HeaderComponent/components/LogoComponent/LogoComponent.vue'
import SearchComponent from '@/components/HeaderComponent/components/SearchComponent/SearchComponent.vue'
import ContentComponent from '@/components/ContentComponent/ContentComponent.vue'
import ShareButton from "@/common/ShareButton/ShareButton.vue"
import { ref } from 'vue';

const contentTitle = ref('This is my test-app');
const contentText = ref('take me to work :-)');
const contentUrl = ref('https://example.com');
</script>

<style scoped>
@import '@/views/HomeView/styles.module.scss';
</style>
