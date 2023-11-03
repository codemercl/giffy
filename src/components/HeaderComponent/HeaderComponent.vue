<template>
  <header class="wrapper">
    <div class="logo">
      <slot name="logo"></slot>
    </div>
    <div class="menu">
      <slot name="menu"></slot>
    </div>
  </header>
</template>

<script setup lang="ts">
</script>

<style scoped>
@import '@/components/HeaderComponent/styles.module.scss';
</style>
