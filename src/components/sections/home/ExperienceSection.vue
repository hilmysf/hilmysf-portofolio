<script setup>
import { EXPERIENCE_LIST } from '../../../const/ExperienceList';
import ExperienceCard from '../../ui/cards/ExperienceCard.vue';
import { useFadeUpMotion } from '@/composables/useFadeUpMotion'
import { ref, onMounted } from 'vue'
import TextButton from '../../ui/widgets/TextButton.vue';
import { useRouter } from 'vue-router'

const router = useRouter()
const experiences = EXPERIENCE_LIST
const expRef = ref(null)
onMounted(() => {
    useFadeUpMotion(expRef, {}, "Experience")
})
function navigateToExperiences() {
    router.push({ name: 'Experience' })
}
const props = defineProps({
    showActionButton: {
        type: Boolean,
        default: false
    }
})
</script>
<template>
    <section id="experience" class="section">
        <div ref="expRef" class="max-w-screen-lg mx-auto w-full">
            <h2 class="text-3xl font-bold text-center text-white">
                Experi<span class="text-primary">ence</span>
            </h2>

            <div class="mt-10 grid gap-6 w-full">
                <ExperienceCard v-for="(exp, i) in experiences" :key="i" v-bind="exp" />
            </div>

            <div class="mt-8 flex justify-center">
                <TextButton v-show="showActionButton" @click="navigateToExperiences" text="View All Experiences &#8594" />
            </div>
        </div>
    </section>

</template>
