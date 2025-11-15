<script setup>
import TechStackCard from '../../ui/cards/TechStackCard.vue'
import { ref, onMounted } from 'vue'
import { useFadeUpMotion } from '@/composables/useFadeUpMotion'
import TextButton from '../../ui/widgets/TextButton.vue'
import { useRouter } from 'vue-router'
const router = useRouter()
import { TECHNOLOGY_LIST } from '@/const/TechStackList.ts'

function navigateToTechStack() {
    router.push({ name: 'TechStack' })
}

const technologies = TECHNOLOGY_LIST

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
        <TextButton v-show="showActionButton" class="mt-4" text="Learn More About My Skills &#8594"
            @click="navigateToTechStack" />
    </section>
</template>