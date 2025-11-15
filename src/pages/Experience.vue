<script setup>
import { EXPERIENCE_LIST } from '../const/ExperienceList';
import ExperienceCard from '../components/ui/cards/ExperienceCard.vue';
import PrimaryButton from '../components/ui/widgets/PrimaryButton.vue';
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
   
        <ExperienceSection/>
</template>