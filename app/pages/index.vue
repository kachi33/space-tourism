<template>
  <main
    class="pt-20 md:pt-28 h-screen flex items-center justify-center md:items-center md:justify-center lg:justify-end lg:items-end lg:pb-20 bg-[url('/assets/home/background-home-mobile.jpg')] lg:bg-[url('/assets/home/background-home-desktop.jpg')] md:bg-[url('/assets/home/background-home-tablet.jpg')] bg-cover bg-no-repeat bg-center"
  >
    <div class="flex flex-col lg:flex-row w-full lg:justify-center items-center h-fit gap-12 md:gap-18 px-4 ">
      <div class="text-center lg:text-left text-light-blue flex flex-col justify-center md:w-2/3 lg:w-1/2 gap-4">
        <span class="font-light leading-[15%] md:text-3xl uppercase tracking-[4px]"> So, you want to travel to </span>
        <h1 class="text-white font-secondary-family text-[80px] md:text-[140px] mb-2">SPACE</h1>
        <p
          class=" px-4 font-accent-family font-normal text-cente lg:max-w-lg lg:text-left leading-[180%] text-[15px]"
        >
          Let’s face it; if you want to go to space, you might as well genuinely
          go to outer space and not hover kind of on the edge of it. Well sit
          back, and relax because we’ll give you a truly out of this world
          experience!
        </p>
      </div>
      <div class="flex justify-center rounded-full border-50 border-transparent hover:border-white/20 items-center">
        <NuxtLink to="/destination" class="rounded-full w-36 h-36 md:w-[20rem] md:h-[20rem] md:text-[32px] uppercase font-accent-family flex items-center justify-center bg-white hover:border-20 border-white/20 text-black">
                Explore
        </NuxtLink>
      </div>
    </div>
  </main>
</template>

<script setup>
useHead({
  title: 'Space Tourism | Home'
})
</script>
