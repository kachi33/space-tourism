<template>
  <main
    class="pt-20 md:pt-28 w-full text-light-blue h-screen bg-[url('/technology/background-technology-mobile.jpg')] lg:bg-[url('/technology/background-technology-desktop.jpg')] md:bg-[url('/technology/background-technology-tablet.jpg')] bg-cover bg-no-repeat bg-center overflow-scroll"
  >
    <div class="container  w-full h-full lg:w-[90%] lg:ml-auto ">
      <div class="flex flex-col h-full text-light-blue gap-4 md:gap-12">
        
        <!-- Title -->
        <h1
          class="text-xl md:text-2xl mb-8 justify-center md:justify-start lg:text-left tracking-[4px] flex gap-2 uppercase"
        >
          <span class="text-gray-400">03</span> Space launch 101
        </h1>

        <!-- Content -->
        <div class="flex flex-col lg:flex-row items-center lg:items-center gap-12 lg:gap-8 flex-grow">
          
          <!-- Image (Mobile: 1st, Desktop: 3rd) -->
          <div class="w-full lg:w-auto flex lg:h-full justify-center lg:justify-end order-1 lg:order-3">
            <div class="w-full max-w-lg md:max-w-none lg:w-full h-64 md:h-80 lg:h-full flex items-center justify-center">
              <!-- Landscape image for desktop -->
              <img
                v-if="isLargeScreen"
                :alt="currentTechnology.name"
                :src="currentTechnology.images?.portrait"
                class="w-full h-full object-contain"
                />
                <!-- Portrait image for mobile/tablet -->
                <img
                v-if="!isLargeScreen"
                :src="currentTechnology.images?.landscape"
                :alt="currentTechnology.name"
                class="w-full h-full object-cover"
              />
            </div>
          </div>

          <!-- Navigation (Mobile: 2nd, Desktop: 1st) -->
          <nav class="order-2 lg:order-1 ">
            <ul class="flex lg:flex-col gap-4 justify-center lg:justify-start">
              <li
                v-for="(item, index) in technology"
                :key="item.name"
                class="cursor-pointer w-10 h-10 md:w-16 md:h-16 lg:w-20 lg:h-20 rounded-full border-2 flex items-center justify-center transition-colors font-secondary-family text-lg md:text-xl lg:text-2xl"
                :class="[
                  currentTechnology.name === item.name
                    ? 'bg-white text-black border-white'
                    : 'bg-transparent text-white border-gray-600 hover:border-white',
                ]"
                @click="selectTechnology(item)"
              >
                {{ index + 1 }}
              </li>
            </ul>
          </nav>

          <!-- Text Content (Mobile: 3rd, Desktop: 2nd) -->
          <div class="text-center lg:text-left order-3 lg:order-2 lg:w-1/2">
            <p class="text-lg md:text-2xl lg:text-3xl  font-secondary-family text-gray-400 uppercase tracking-wider mb-2">
              The terminology...
            </p>
            
            <h2 class="text-3xl md:text-5xl lg:text-6xl font-secondary-family mb-6 text-white uppercase">
              {{ currentTechnology.name }}
            </h2>
            
            <p class="px-2 py-4 lg:text-lg font-accent-family text-light-blue leading-relaxed max-w-lg  mx-auto lg:mx-0">
              {{ currentTechnology.description }}
            </p>
          </div>
          
        </div>
      </div>
    </div>
  </main>
</template>

<script setup>
useHead({
  title: 'Space Tourism | Technology'
})

const technology = [
  {
    name: "Launch vehicle",
    images: {
      portrait: "/technology/image-launch-vehicle-portrait.jpg",
      landscape: "/technology/image-launch-vehicle-landscape.jpg"
    },
    description: "A launch vehicle or carrier rocket is a rocket-propelled vehicle used to carry a payload from Earth's surface to space, usually to Earth orbit or beyond. Our WEB-X carrier rocket is the most powerful in operation. Standing 150 metres tall, it's quite an awe-inspiring sight on the launch pad!"
  },
  {
    name: "Spaceport",
    images: {
      portrait: "/technology/image-spaceport-portrait.jpg",
      landscape: "/technology/image-spaceport-landscape.jpg"
    },
    description: "A spaceport or cosmodrome is a site for launching (or receiving) spacecraft, by analogy to the seaport for ships or airport for aircraft. Based in the famous Cape Canaveral, our spaceport is ideally situated to take advantage of the Earth's rotation for launch."
  },
  {
    name: "Space capsule",
    images: {
      portrait: "/technology/image-space-capsule-portrait.jpg",
      landscape: "/technology/image-space-capsule-landscape.jpg"
    },
    description: "A space capsule is an often-crewed spacecraft that uses a blunt-body reentry capsule to reenter the Earth's atmosphere without wings. Our capsule is where you'll spend your time during the flight. It includes a space gym, cinema, and plenty of other activities to keep you entertained."
  }
]

const currentTechnology = ref(technology[0])

const isLargeScreen = ref(false)

const updateScreenSize = () => {
  if (process.client) {
    isLargeScreen.value = window.innerWidth >= 1024
  }
}

const selectTechnology = (item) => {
  currentTechnology.value = item
  if (process.client) {
    try {
      sessionStorage.setItem('selectedTechnology', JSON.stringify(item))
    } catch (e) {}
  }
}

onMounted(() => {
  if (process.client) {
    updateScreenSize()
    window.addEventListener('resize', updateScreenSize)
    
    try {
      const saved = sessionStorage.getItem('selectedTechnology')
      if (saved) {
        const savedTechnology = JSON.parse(saved)
        const found = technology.find(t => t.name === savedTechnology.name)
        if (found) {
          currentTechnology.value = found
        }
      }
    } catch (e) {}
  }
})

onUnmounted(() => {
  if (process.client) {
    window.removeEventListener('resize', updateScreenSize)
  }
})
</script>
