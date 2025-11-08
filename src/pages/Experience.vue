<script setup>
import { EXPERIENCE_LIST } from '../const/ExperienceList';
import ExperienceCard from '../components/ui/ExperienceCard.vue';
import PrimaryButton from '../components/ui/PrimaryButton.vue';
import { useFadeUpMotion } from '@/composables/useFadeUpMotion'
import { ref, onMounted } from 'vue'
import ExperienceSection from '../components/sections/home/ExperienceSection.vue'
const experiences = EXPERIENCE_LIST
const expRef = ref(null)
onMounted(() => {
    useFadeUpMotion(expRef, {}, "Experience")
})
</script>
<template>
   
        <ExperienceSection class="md:!pt-32" />
</template>