<script setup>
import TechStackCard from '../../ui/TechStackCard.vue'

import icAndroid from '@/assets/ic_android.png'
import icCompose from '@/assets/ic_compose.png'
import icFlutter from '@/assets/ic_flutter.png'
import icJava from '@/assets/ic_java.png'
import icSwift from '@/assets/ic_swift.png'
import icVue from '@/assets/ic_vue.png'
import icJs from '@/assets/ic_javascript.png'
import icKotlin from '@/assets/ic_kotlin.png'
import { ref, onMounted } from 'vue'
import { useFadeUpMotion } from '@/composables/useFadeUpMotion'
import TextButton from '../../ui/TextButton.vue'
import { useRouter } from 'vue-router'
const router = useRouter()

function navigateToTechStack() {
    router.push({ name: 'TechStack' })
}

const technologies = [
    { title: 'Android', src: icAndroid },
    { title: 'Jetpack Compose', src: icCompose },
    { title: 'Kotlin', src: icKotlin },
    { title: 'Java', src: icJava },
    { title: 'Flutter', src: icFlutter },
    { title: 'Swift', src: icSwift },
    { title: 'Vue.js', src: icVue },
    { title: 'Javascript', src: icJs },
]

const isMobile = ref(window.innerWidth < 640)

function handleResize() {
    isMobile.value = window.innerWidth < 640 // sm breakpoint
}

const techStackRef = ref(null)

onMounted(() => {
    window.addEventListener('resize', handleResize)
    useFadeUpMotion(techStackRef, {}, "Tech")
})

const props = defineProps({
    showActionButton: {
        type: Boolean,
        default: false
    }
})
</script>

<template>
    <section id="tech_stack" class="section">
        <div ref="techStackRef" class="max-w-screen-lg w-full">
            <h1 class="text-3xl font-bold">Tech <span class="text-primary">Stack</span>
            </h1>
            <div class="mt-10 grid grid-cols-2 lg:grid-cols-4 gap-x-4 gap-y-4 ">
                <div v-for="(tech, i) in (isMobile ? technologies.slice(0, 4) : technologies)" :key="i">
                    <TechStackCard :title="tech.title" :src="tech.src" />
                </div>
            </div>
        </div>
        <TextButton v-show="showActionButton" class="mt-4" text="Learn More About My Skills &#8594" @click="navigateToTechStack" />
    </section>
</template>