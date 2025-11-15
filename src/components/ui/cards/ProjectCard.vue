<script setup>
import MediaViewer from '@/components/ui/widgets/MediaViewer.vue';

// const props = defineProps({
//     title: { type: String, required: true, default: "" },
//     desc: { type: String, required: true, default: "" },
//     type: { type: String, required: true, default: "" },
//     mediaPreview: { type: String, required: false, default: null },
//     sourceCode: { type: String, required: false, default: null },
// })
const props = defineProps({
    project: {
        type: Object,
        required: true
    },
})

const emit = defineEmits(["click"])
console.log(props.project)
</script>
<template>
    <div @click="emit('click', project)" class="max-w-xl">
        <MediaViewer class="flex w-full h-auto object-contain" :src="project.mediaPreview" />
        <div class="flex justify-between items-center mt-2">
            <h1 class="text-lg">
                {{ project.title }}
            </h1>
            <h2 class="text-sm text-surface font-bold bg-primary rounded-md px-2 py-1">
                {{ project.type }}
            </h2>
        </div>
        <p class="text-start text-sm text-gray-400 mt-1">{{ project.desc }}</p>
    </div>
</template>