<template>
  <main class="wrapper">
    <router-link v-for="gif in searchList" :to="'/gif/' + gif.id" :key="gif.id" class="element">
      <img
        :src="gif.images?.original?.url ? gif.images?.original?.url : gif?.embed_url"
        :alt="gif.images?.original?.url ? 'Search Gif' : ''"
      />
    </router-link>
  </main>
</template>

<script setup lang="ts">
import { useDataList } from '@/hooks/useDataList.js'
import { searchGifData } from '@/stores/modules/searchModule/search.service';
import { getRandomWord } from '@/utils/randomWord';
import { useScroll } from '@/hooks/useScroll'; 
import { useStore } from 'vuex';
const { searchList } = useDataList()
const store = useStore()

useScroll(searchList, searchGifData, getRandomWord);
</script>

<style scoped>
@import '@/components/ContentComponent/styles.module.scss';
</style>