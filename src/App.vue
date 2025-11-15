<script setup lang="ts">
import DefaultLayout from './components/layout/DefaultLayout.vue';
import ScrollToTopButton from './components/ui/widgets/ScrollToTopButton.vue';
</script>

<template>
  <DefaultLayout>
    <router-view />
  </DefaultLayout>
  <ScrollToTopButton />
</template>