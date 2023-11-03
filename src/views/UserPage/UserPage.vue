<template>
  <section class="userpage">
    <HeaderComponent>
      <template #logo>
        <component :is="LogoComponent" :link="true" />
      </template>
    </HeaderComponent>
    <main class="container" v-for="gif in gifData" :key="gif.id">
      <div class="pic">
        <iframe :src="gif.user?.avatar_url" />
      </div>
      <div class="content">
        <h1>{{ gif?.user?.display_name }}</h1>
        <h2>@{{ gif?.user?.username }}</h2>
        <a :href="gif.user?.profile_url">{{ gif.user?.profile_url }}</a>
      </div>
    </main>
  </section>
</template>

<script setup lang="ts">
import LogoComponent from '@/components/HeaderComponent/components/LogoComponent/LogoComponent.vue'
import HeaderComponent from '@/components/HeaderComponent/HeaderComponent.vue'
import type { CartData } from '@/stores/modules/getByIdModule/types'
import { onMounted, ref } from 'vue'
import { useRoute } from 'vue-router'
import { useStore } from 'vuex'

const route = useRoute()
const store = useStore()

const gifData = ref<CartData[]>([])
const id = route.params.id

onMounted(async () => {
  store.commit('setParamId', id)
  await store.dispatch('fetchDataCart')
  gifData.value = store.state.getById
})
</script>
<style scoped>
@import '@/views/UserPage/styles.module.scss';
</style>
