<script setup>
import { onMounted, onUnmounted, ref } from 'vue';
import PrimaryButton from '../ui/PrimaryButton.vue';
import ProgressBar from '../ui/ProgressBar.vue';

const isMenuOpen = ref(false)
const isScrolled = ref(false)
const scrollProgress = ref(0)
const isMobile = ref(window.innerWidth < 640)
const selectedPage = ref('/')

function handleResize() {
    isMobile.value = window.innerWidth < 640 // sm breakpoint
}

const handleScroll = () => {
    const scrollTop = window.scrollY
    const docHeight = document.documentElement.scrollHeight - window.innerHeight
    const progress = (scrollTop / docHeight) * 100
    scrollProgress.value = Math.min(Math.max(progress, 0), 100)
    isScrolled.value = scrollTop > 0
}

const closeMenu = () => {
    isMenuOpen.value = false
}

onMounted(() => {
    window.addEventListener('scroll', handleScroll)
    window.addEventListener('resize', handleResize)
})

onUnmounted(() => {
    window.removeEventListener('scroll', handleScroll)
    window.removeEventListener('resize', handleResize)
})

const setSelectedPage = (page) => {
    selectedPage.value = page
}
</script>
<template>
    <!-- Progress Bar -->
    <ProgressBar :scrollProgress="scrollProgress" />

    <!-- Nav Bar except small screen-->
    <div class="flex justify-center">
        <nav v-show="!isMobile" :class="[
            'fixed z-[100] top-5 mx-auto px-4 py-3 flex justify-center gap-2 sm:gap-0 items-center transition-colors duration-500 rounded-full backdrop-blur-sm',
            isScrolled ? 'bg-[rgba(14,14,14,0.75)]' : 'bg-[rgba(14,14,14,0.15)]',
        ]">
            <div>
                <router-link to="/" @click="setSelectedPage('/contact')" class="nav-link">Home</router-link>
                <router-link to="/projects" @click="setSelectedPage('/projects')"
                    class="nav-link">Projects</router-link>
                <router-link to="/experience" @click="setSelectedPage('/experience')"
                    class="nav-link">Experience</router-link>
                <router-link to="/about" @click="setSelectedPage('/about')" class="nav-link">About</router-link>
                <router-link to="/contact">
                    <PrimaryButton text="Let's Talk" @click="setSelectedPage('/contact')" />
                </router-link>
            </div>

        </nav>
    </div>

    <!-- Nav Bar for small screen-->
    <div :class="[
        'sm:hidden fixed z-[100] justify-center items-center w-full',
        isMenuOpen ? 'bg-[rgba(14,14,14,0.75)]' : 'bg-transparent'
    ]">
        <Transition>
            <button @click="isMenuOpen = !isMenuOpen"
                class="m-2 text-primary animate-scale rounded-lg p-2 active:text-primary">
                <svg class="w-6 h-6" fill="none" stroke="currentColor" viewBox="0 0 24 24">
                    <path v-if="!isMenuOpen" stroke-linecap="round" stroke-linejoin="round" stroke-width="2"
                        d="M4 6h16M4 12h16M4 18h16" />
                    <path v-else stroke-linecap="round" stroke-linejoin="round" stroke-width="2"
                        d="M6 18L18 6M6 6l12 12" />
                </svg>
            </button>
        </Transition>
       <Transition class="slide-fade">
         <div v-show="isMenuOpen" class="flex flex-col bg-transparent">
            <router-link @click="closeMenu" to="/" class="nav-link menu-item">Home</router-link>
            <router-link @click="closeMenu" to="/projects" class="nav-link menu-item">Projects</router-link>
            <router-link @click="closeMenu" to="/experience" class="nav-link menu-item">Experience</router-link>
            <router-link @click="closeMenu" to="/about" class="nav-link menu-item">About</router-link>
            <router-link @click="closeMenu" to="/contact" class="nav-link menu-item">Let's Talk</router-link>
        </div>
       </Transition>
    </div>
</template>

<style scoped>
.nav-link {
    @apply text-gray-700 hover:text-primary-hover cursor-pointer font-medium px-3 sm:text-sm;
    color: var(--color-text);
}

.router-link-exact-active {
    @apply text-primary font-semibold;
}

.menu-item {
    /* background: black; */
    background: rgba(14,14,14,0.90);
    border-radius: 1px;
    border-color: gray;
    color: var(--color-primary) !;
    padding: 16px;
    font-size: 12px;
    text-align: center;
}

.slide-fade-enter-active { 
  transition: all 0.4s ease;
}
.slide-fade-leave-active {
  transition: all 0.3s ease;
}
.slide-fade-enter-from {
  opacity: 0;
  transform: translateY(-20px);
}
.slide-fade-leave-to {
  opacity: 0;
  transform: translateY(-20px);
}
</style>