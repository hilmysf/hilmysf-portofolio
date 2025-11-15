<script setup>
import { useRoute, useRouter } from 'vue-router'
import { PROJECT_LIST } from '@/const/ProjectList'
import MediaViewer from '@/components/ui/widgets/MediaViewer.vue';
import icGithub from '@/assets/ic_github_white.png'

const route = useRoute()
const router = useRouter()
const id = route.params.id
const project = PROJECT_LIST.find((item) => item.id === id)

function navigateToProjects() {
    router.push({
        name: 'Projects'
    })
}
</script>
<template>
    <section class="section">
        <div class="flex flex-col items-start max-w-screen-md w-full ">
            <h1 class="mb-4">
                {{ project?.title }}
            </h1>
            <p>{{ project?.desc }}</p>
            <MediaViewer class="w-full h-auto object-contain mb-4" :src="project?.mediaPreview" />
            <h2>About This Project</h2>
            <p>{{ project?.desc }}</p>
            <div v-show="project?.features.length > 0" class="items-start flex flex-col">
                <h2>Key Features</h2>
                <div class="mb-4 cursor-pointer text-start">
                    <p class="!mb-0" v-for="feature in project?.features">
                        • {{ feature }}
                    </p>
                </div>
            </div>
            <div v-show="project?.sourceCode != null">
                <h2>Link & Resources</h2>
                <a :href="project?.sourceCode" target="_blank"
                    class="animate-scale text-text text-sm rounded-lg border-text border bg-surface px-2 py-1 mt-2 mb-4 flex items-center"><img
                        :src="icGithub" alt="Source Code" class="w-6 h-6 mr-2" />
                    Source Code</a>
            </div>
            <h2>Tech Stack</h2>
            <div class="cursor-pointer flex flex-row gap-2">
                <div class="animate-scale text-text text-sm rounded-lg border-text border bg-surface px-2 py-1 mt-2 mb-4"
                    v-for="tech in project.techs" :key="tech">
                    {{ tech }}</div>
            </div>
            <h2>Other Information</h2>
            <div class="cursor-pointer flex flex-row gap-2">
                <div class="animate-scale text-text text-sm rounded-lg border-text border bg-surface px-2 py-1 mt-2 mb-4"
                    v-for="tag in project.tags" :key="tag">
                    {{ tag.toTitleCase() }}</div>
            </div>
            <hr class="mb-4" />
            <h2>See My Other Projects</h2>
            <button @click="navigateToProjects"
                class="text-text text-sm rounded-lg border-text border bg-surface px-2 py-1 mt-2 mb-4 flex items-center animate-scale">
                ← View All Projects
            </button>
        </div>
    </section>
</template>

<style scoped>
h2 {
    font-size: large;
    font-weight: 500;
    color: var(--color-text);
    margin-bottom: 0.25rem;
}

p {
    margin-bottom: 1rem;
    font-weight: 400;
    font-size: medium;
    color: var(--color-text-muted);

}
</style>