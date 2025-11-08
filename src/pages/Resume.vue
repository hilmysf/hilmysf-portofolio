<script setup>
import cv from '@/assets/files/cv_hilmy.pdf'
</script>
<template>
  <section class="section flex flex-col items-center justify-center">
    <div class="max-w-screen-md w-full flex flex-col flex-1 p-0 sm:p-16">
      <h1 class="mb-4 text-3xl font-bold">Res<span class="text-primary">ume</span></h1>
      <iframe class="flex-1 w-full border rounded" :src="cv"></iframe>
    </div>
  </section>
</template>