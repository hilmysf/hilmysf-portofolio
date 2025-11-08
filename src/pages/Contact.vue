<script setup>
import Input from '@/components/ui/Input.vue';
import PrimaryButton from '../components/ui/PrimaryButton.vue';
import { useFadeUpMotion } from '@/composables/useFadeUpMotion'
import { ref, onMounted } from 'vue'
const titleRef = ref(null)
const formRef = ref(null)
onMounted(() => {
    useFadeUpMotion(titleRef, {}, "Hero")
    useFadeUpMotion(formRef, {}, "Hero")
})
</script>
<template>
    <section id="contact" class="section">
        <h1 ref="titleRef" class="text-3xl font-bold text-center text-white mb-4">Contact <span
                class="text-primary">Me</span></h1>
        <form ref="formRef"  class="space-y-4" action="https://api.web3forms.com/submit" method="POST">
            <input type="hidden" name="access_key" value="4f50abd5-2792-40c2-ba24-4d16c26d56a0">
            <Input type="text" name="name" placeholder="Your Name" required />
            <Input type="email" name="email" placeholder="Your Email" required />
            <Input type="text" name="message" placeholder="Your Message..." required line="5"></Input>
            <PrimaryButton class="w-full" text="Send" type="submit" />
        </form>
    </section>
</template>