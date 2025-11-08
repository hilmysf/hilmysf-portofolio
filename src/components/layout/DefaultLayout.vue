<script setup lang="ts">
import Footer from './Footer.vue';
import NavBar from './NavBar.vue';
import FireflyAnimation from '@/components/animations/FireflyAnimation.vue';

</script>

<template>
    <div class="min-h-screen flex flex-col">
        <NavBar />

        <main class="flex-1">
            <FireflyAnimation/>
            <slot></slot>
        </main>
        <Footer></Footer>
    </div>
</template>