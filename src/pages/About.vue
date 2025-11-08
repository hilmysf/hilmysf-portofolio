<script setup>
import Input from '@/components/ui/Input.vue';
import PrimaryButton from '../components/ui/PrimaryButton.vue';
import ProfilePhoto from '@/assets/images/Hilmy-Gunung Gede.jpeg'
</script>
<template>
    <section id="about" class="section">
        <div class="flex flex-col md:flex-row justify-center max-w-screen-lg my-10">
            <div class="flex-[2] flex-col text-left">
                <h1 class="md:text-7xl mb-4">About Me</h1>
                <h3 class="md:text-xl font-normal text-primary mb-5">A fast learner with a curious mind, always eager to
                    explore new technologies and solve complex problems.</h3>
                <div class="space-y-2 text-justify">
                    <p class="sm:text-xs md:text-base">
                        Hi, my name is Hilmy Saeful Fatah — but you can just call me Hilmy.
                        I'm a Front-End Developer passionate about creating meaningful digital products that make a real
                        impact on users.
                    </p>

                    <p>
                        I enjoy receiving feedback and using it to continuously improve product quality and user
                        experience.
                    </p>

                    <p>
                        Currently, I work at PT Pupuk Indonesia, where I develop AI-powered Android applications
                        to support business needs and enhance user convenience.
                    </p>

                    <p>
                        In my daily work, I focus on building mobile applications using Flutter and Android,
                        while also expanding my knowledge in front-end web technologies such as Vue.js and Next.js.
                        My experience in mobile development helps me better understand design principles and user
                        interactions on the web.
                    </p>

                    <p>
                        I’m deeply interested in crafting interfaces that are intuitive, visually appealing,
                        and aligned with business goals. For me, every day is an opportunity to learn and become a
                        better
                        developer and human being :)
                    </p>
                </div>
            </div>
            <div class="w-10 mt-4 sm:mt-0 "></div>
            <div class="flex flex-[1] justify-center items-center">
                <img :src="ProfilePhoto" alt="Profile Photo"
                    class="scale-100 sm:scale-100 grayscale border-primary border-2 rounded lg shadow-[0_0_10px_1px_rgba(250,204,21,0.6)]" />
            </div>
        </div>
    </section>
</template>

<style scoped>
p {
    @apply text-xs sm:text-sm md:text-base;
}
</style>