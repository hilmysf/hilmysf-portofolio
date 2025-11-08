<script setup>
import MediaViewer from './MediaViewer.vue';

const props = defineProps({
    title: { type: String, required: true, default: "" },
    desc: { type: String, required: true, default: "" },
    type: { type: String, required: true, default: "" },
    mediaPreview: { type: String, required: false, default: null },
    sourceCode: { type: String, required: false, default: null },
})
</script>
<template>
    <div class="max-w-xl">
        <MediaViewer class="flex w-full h-auto object-contain"
            src="https://storage.googleapis.com/gweb-uniblog-publish-prod/original_images/tenor_1.gif" />
        <div class="flex justify-between items-center mt-2">
            <h1 class="text-lg">
                {{ title }}
            </h1>
            <h2 class="text-base text-surface font-bold bg-primary rounded-full px-3 py-0">
                {{ type }}
            </h2>
        </div>
        <p class="text-start text-sm text-gray-400 mt-1">{{ desc }}</p>
    </div>
</template>