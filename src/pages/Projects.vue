<script setup>
import { useFadeUpMotion } from '@/composables/useFadeUpMotion'
import { ref, onMounted } from 'vue'
import ProjectSection from '@/components/sections/home/ProjectsSection.vue'
const projectRef = ref(null)
onMounted(() => {
    useFadeUpMotion(projectRef, {}, "Projects")
})
</script>
<template>

    <ProjectSection class="md:!pt-32" />
</template>