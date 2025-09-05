<template>
  <main
    class="pt-20 md:pt-28 h-screen flex items-center justify-center bg-[url('/assets/home/background-home-mobile.jpg')] lg:bg-[url('/assets/home/background-home-desktop.jpg')] md:bg-[url('/assets/home/background-home-tablet.jpg')] bg-cover bg-no-repeat bg-center"
  >
    <div class="flex flex-col items-center justify-center text-center text-white px-4 gap-8">
      <div class="text-light-blue">
        <h1 class="text-6xl text-white md:text-8xl lg:text-9xl font-secondary-family mb-4">404</h1>
        <h2 class="text-2xl md:text-4xl font-secondary-family tracking-wider uppercase mb-4">
          Page Not Found
        </h2>
        <p class="text-lg font-accent-family text-light-blue leading-relaxed max-w-md">
          We have a problem. The page you're looking for seems to have drifted into space.
        </p>
      </div>
      
      <div class="flex flex-col sm:flex-row gap-4">
        <NuxtLink 
          to="/" 
          class="px-8 py-4 bg-white text-black font-accent-family uppercase tracking-wider rounded-full hover:bg-white/90 transition-colors"
        >
          Return Home
        </NuxtLink>
        
        <button 
          @click="$router.back()" 
          class="px-8 py-4 border-2 border-white text-white font-accent-family uppercase tracking-wider rounded-full hover:bg-white hover:text-black transition-colors"
        >
          Go Back
        </button>
      </div>
    </div>
  </main>
</template>

<script setup>
import { useError } from '#app'

useHead({
  title: 'Space Tourism | Page Not Found'
})

const error = useError()
</script>