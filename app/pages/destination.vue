<template>
  <main
    class="pt-20 md:pt-28 text-light-blue h-screen bg-[url('/destination/background-destination-mobile.jpg')] lg:bg-[url('/destination/background-destination-desktop.jpg')] md:bg-[url('/destination/background-destination-tablet.jpg')] bg-cover bg-no-repeat bg-center overflow-scroll"
  >
    <div class="container md:w-[80%] lg:h-full mx-auto px-4 py-8">
      <div class="flex flex-col lg:h-full justify-center text-light-blue md:gap-12">
        <h1 class="text-xl md:text-2xl mb-8 text-center lg:text-left tracking-[4px] flex justify-center md:justify-start gap-2 uppercase">
            <span class="text-gray-400">01</span>Pick your destination
        </h1>

        <div class="flex flex-col lg:flex-row justify-center items-center lg:h-full gap-12 lg:gap-24">
          <div class="lg:w-1/2 flex justify-center">
            <img 
            :src="currentDestination.images?.png" 
            :alt="currentDestination.name"
            class="w-46 h-46 md:w-80 md:h-80 lg:w-96 lg:h-96 object-contain"
            />
          </div>
          
          <div class="lg:w-1/2 text-white">
            <nav class="mb-8">
              <ul class="flex font-secondary-family gap-6 justify-center text-light-blue lg:justify-start">
                <li 
                v-for="destination in destinations" 
                :key="destination.name"
                class="cursor-pointer pb-2 border-b-2 transition-colors"
                :class="[
                  currentDestination.name === destination.name 
                  ? 'border-white text-white' 
                  : 'border-transparent hover:border-white'
                ]"
              @click="selectDestination(destination)"
              >
              {{ destination.name.toUpperCase() }}
            </li>
          </ul>
        </nav>
        
        <div class="text-center lg:text-left">
          <h2 class="text-6xl md:text-8xl font-secondary-family mb-6">
            {{ currentDestination.name?.toUpperCase() }}
          </h2>
          
          <p class="text-lg font-accent-family mb-8 text-light-blue leading-relaxed mx-auto lg:mx-0">
            {{ currentDestination.description }}
          </p>
          
          <div class="border-t border-gray-600 pt-6">
            <div class="flex flex-col md:flex-row gap-8 justify-center lg:justify-start">
              <div>
                <p class="text-sm text-gray-400 mb-2 tracking-wider">AVG. DISTANCE</p>
                <p class="text-2xl uppercase font-secondary-family">{{ currentDestination.distance }}</p>
              </div>
              <div>
                <p class="text-sm text-gray-400 mb-2 tracking-wider">EST. TRAVEL TIME</p>
                <p class="text-2xl uppercase font-secondary-family">{{ currentDestination.travel }}</p>
              </div>
            </div>
          </div>
        </div>
      </div>
    </div>
      </div>
    </div>
  </main>
</template>

<script setup>
useHead({
  title: 'Space Tourism | Destination'
})

const destinations = [
  {
    name: "Moon",
    images: {
      png: "/destination/image-moon.png",
      webp: "/destination/image-moon.webp"
    },
    description: "See our planet as you've never seen it before. A perfect relaxing trip away to help regain perspective and come back refreshed. While you're there, take in some history by visiting the Luna 2 and Apollo 11 landing sites.",
    distance: "384,400 km",
    travel: "3 days"
  },
  {
    name: "Mars",
    images: {
      png: "/destination/image-mars.png",
      webp: "/destination/image-mars.webp"
    },
    description: "Don't forget to pack your hiking boots. You'll need them to tackle Olympus Mons, the tallest planetary mountain in our solar system. It's two and a half times the size of Everest!",
    distance: "225 mil. km",
    travel: "9 months"
  },
  {
    name: "Europa",
    images: {
      png: "/destination/image-europa.png",
      webp: "/destination/image-europa.webp"
    },
    description: "The smallest of the four Galilean moons orbiting Jupiter, Europa is a winter lover's dream. With an icy surface, it's perfect for a bit of ice skating, curling, hockey, or simple relaxation in your snug wintery cabin.",
    distance: "628 mil. km",
    travel: "3 years"
  },
  {
    name: "Titan",
    images: {
      png: "/destination/image-titan.png",
      webp: "/destination/image-titan.webp"
    },
    description: "The only moon known to have a dense atmosphere other than Earth, Titan is a home away from home (just a few hundred degrees colder!). As a bonus, you get striking views of the Rings of Saturn.",
    distance: "1.6 bil. km",
    travel: "7 years"
  }
]

const currentDestination = ref(destinations[0])

const selectDestination = (destination) => {
  currentDestination.value = destination
  if (process.client) {
    try {
      sessionStorage.setItem('selectedDestination', JSON.stringify(destination))
    } catch (e) {}
  }
}

onMounted(() => {
  if (process.client) {
    try {
      const saved = sessionStorage.getItem('selectedDestination')
      if (saved) {
        const savedDestination = JSON.parse(saved)
        const found = destinations.find(d => d.name === savedDestination.name)
        if (found) {
          currentDestination.value = found
        }
      }
    } catch (e) {}
  }
})
</script>