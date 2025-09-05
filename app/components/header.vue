<template>
  <nav class="fixed z-50 flex items-center font- justify-between w-full lg:mt-6 p-6 md:p-0">
    <!-- p-6 md:px-12 lg:px-24 xl:px-32 2xl:px-40 -->
     <NuxtLink to="/"  class="flex items-center justify-center md:w-1/4  ">
    <img
      src="/shared/logo.svg"
      alt="logo"
        class="w-12 h-12 object-cover md:mx-10 md:my-6"
    />
    </NuxtLink>
    <hr class="hidden lg:block w-2/3 -mr-10 z-50 border-t border-white/30 " />
    <img 
      src="/shared/icon-hamburger.svg"
      alt="menu"
      class="h-6 w-6 md:hidden"
      @click="toggleMenu"
    />
    <div class="relative" v-if="isMenuOpen">
      <div
        class="fixed inset-0 bg-black/0 z-40"
        @click="isMenuOpen = false"
      ></div>
      <div class="fixed top-0 right-0 w-2/3 h-full backdrop-filter backdrop-blur-lg bg-white/5 z-50 flex flex-col gap-10 ">
        <img
          src="/shared/icon-close.svg"
          alt="close"
          class="h-6 w-6 mb-6 mt-8 mr-6 text-right ml-auto cursor-pointer"
          @click="isMenuOpen = false"
        />
        <ul class="flex flex-col gap-8 text-white pl-6 text-lg ">
          <NuxtLink 
            v-for="item in navItemsMobile" 
            :key="item.path" 
            :to="item.path" 
            class="cursor-pointer"
          >
            <li :class="['hover:border-r-4 flex-2 border-white', { 'border-r-4': $route.path === item.path }]">
              <span class="font-extrabold">{{ item.number }}</span>  {{ item.name }}
            </li>
          </NuxtLink>
        </ul>
      </div>
    </div>
    <div class="hidden md:flex justify-end  backdrop-filter w-full backdrop-blur-md bg-white/10 pr-10">
        <ul
            class="hidden h-full md:flex md:gap-10 lg:gap-10 xl:gap-16 2xl:gap-20 text-lg "
        >
            <NuxtLink 
              v-for="item in navItems" 
              :key="item.path" 
              :to="item.path"
            >
              <li :class="['hover:border-b-2 h-full text-white  py-8 lg:py-6 flex gap-4 border-white', { 'border-b-2': $route.path === item.path }]">
               <span class="font-bold">{{ item.number }} </span>{{ item.name }}
              </li>
            </NuxtLink>
        </ul>
    </div>
  </nav>
</template>
<script setup>
import { ref } from "vue";

const isMenuOpen = ref(false);

const navItems = [
  { path: '/',  name: 'HOME' },
  { path: '/destination/', number: '01', name: 'DESTINATION' },
  { path: '/crew/', number: '02', name: 'CREW' },
  { path: '/technology/', number: '03', name: 'TECHNOLOGY' }
];


const navItemsMobile = [
      { path: '/', number: '00', name: 'HOME' },
  { path: '/destination', number: '01', name: 'DESTINATION' },
  { path: '/crew', number: '02', name: 'CREW' },
  { path: '/technology', number: '03', name: 'TECHNOLOGY' }
];

const toggleMenu = () => {
  isMenuOpen.value = !isMenuOpen.value;
};
</script>
