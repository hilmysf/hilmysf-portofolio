<script setup lang="ts">
import ProjectCard from '../../ui/cards/ProjectCard.vue';
import { useFadeUpMotion } from '../../../composables/useFadeUpMotion'
import { ref, onMounted, computed } from 'vue'
import { PROJECT_LIST } from '@/const/ProjectList.ts'
import TextButton from '../../ui/widgets/TextButton.vue'
import { useRouter } from 'vue-router'

//Type: personal,cwork, academic, freelance
let projects = PROJECT_LIST

const router = useRouter()

function navigateToProjects() {
    router.push({ name: 'Projects' })
}

const projectRef = ref(null)
onMounted(() => {
    useFadeUpMotion(projectRef, {}, "Projects")
})
const props = defineProps({
    showActionButton: {
        type: Boolean,
        default: false
    }
})

const limitedProjects = computed(() => {
    return projects.slice(0, props.showActionButton ? 4 : projects.length)
})

const handleClick = (project) => {
    router.push({
        name: 'ProjectDetail',
        params: { id: project.id }
    })
}


</script>

<template>
    <section id="projects" class="section">
        <div ref="projectRef" class="flex flex-col max-w-screen-lg w-full items-center">
            <h2 class="text-3xl font-bold ">Latest <span class="text-primary">Projects</span></h2>
            <div class="grid grid-cols-1 lg:grid-cols-2 gap-6 mt-10">
                <ProjectCard v-for="(project, i) in limitedProjects" :key="i" :project="project"
                    @click="handleClick" />
            </div>
            <TextButton v-show="showActionButton" @click="navigateToProjects" class="flex flex-col mt-4"
                text="View All Projects &#8594" />
        </div>
    </section>
</template>