<script setup>
import PrimaryButton from '../../ui/widgets/PrimaryButton.vue';
import OutlinedButton from '../../ui/widgets/OutlinedButton.vue'
import { useFadeUpMotion } from '@/composables/useFadeUpMotion'
import { ref, onMounted } from 'vue'
import { useRouter } from 'vue-router'

const heroRef = ref(null)
const router = useRouter()

function navigateToProjects() {
    router.push({ name: 'Projects' })
}

function navigateToResume() {
    router.push({ name: 'Resume' })
}


onMounted(() => {
    useFadeUpMotion(heroRef, {}, "Hero")
})
</script>
<template>
    <section id="home" class="section">
        <div ref="heroRef" class="max-w-screen-lg w-full">
            <h3 class="text-xl font-normal text-text-muted">Turning ideas into seamless digital experiences.</h3>
            <h1
                class="mt-10 text-5xl font-extrabold bg-gradient-to-r from-white via-white to-primary bg-clip-text text-transparent">
                BUILDING MOBILE IMPACT</h1>
            <h2 class="italic text-primary text-2xl mt-8">code with purpose, design with
                empathy</h2>
            <div class="flex flex-col md:flex-row justify-center mt-6 gap-2">
                <PrimaryButton text="View My Work" @click="navigateToProjects" />
                <OutlinedButton text="Download CV" @click="navigateToResume" />
            </div>
        </div>
    </section>
</template>