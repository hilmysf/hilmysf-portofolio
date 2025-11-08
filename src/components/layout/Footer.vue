<script setup>

import icLinkedin from '@/assets/ic_linkedin_white.png'
import icGithub from '@/assets/ic_github_white.png'

const socialMedia = [
    { url: 'https://www.linkedin.com/in/hilmysf/', icon: icLinkedin },
    { url: 'https://github.com/hilmysf', icon: icGithub }
]
</script>

<template>
    <footer class="border-t border-primary bg-background">
        <div class="flex justify-center flex-col items-center py-6">
            <h1 class="text-3xl mb-4">Connect with me</h1>
            <div class="flex gap-4 justify-center">
                <a target="_blank" rel="noopener noreferrer" v-for="(icon, i) in socialMedia" :key="i" :href="icon.url">
                    <img :src="icon.icon" width="48px"></img>
                </a>
            </div>
        </div>
        <hr class="border-t border-gray-900" />
        <div class="bg-black px-4 py-3">
            <p>&copy; 2025 Hilmy Saeful Fatah. All rights reserved.</p>
        </div>
    </footer>
</template>