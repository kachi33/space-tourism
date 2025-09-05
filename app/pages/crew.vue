<template>
  <main
    class="pt-20 md:pt-28 text-light-blue h-screen bg-[url('/crew/background-crew-mobile.jpg')] md:bg-[url('/crew/background-crew-tablet.jpg')] lg:bg-[url('/crew/background-crew-desktop.jpg')] bg-cover bg-no-repeat bg-center overflow-scroll"
  >
    <div class="container lg:w-4/5 h-full mx-auto px-4 py-8">
      <div class="flex flex-col h-full text-light-blue gap-4 md:gap-12">
        
        <!-- Title -->
        <h1
          class="text-xl md:text-2xl mb-8 justify-center md:justify-start lg:text-left tracking-[4px] flex gap-2 uppercase"
        >
          <span class="text-gray-400">02</span> Meet your crew
        </h1>

        <!-- Content -->
        <div class="flex flex-col lg:flex-row items-center md:justify-between lg:items-end gap-12 lg:gap-2 flex-grow">
          
          <!-- Left (Text + Pagination) -->
          <div class="lg:w-1/2 flex flex-col justify-between lg:h-full">
            <div class="text-center flex flex-col lg:justify-center h-full md:gap-4 lg:text-left">
              <p class="text-xl md:text-2xl font-secondary-family text-gray-400 uppercase">
                {{ currentCrew.role }}
              </p>

              <h2 class="text-3xl md:text-5xl lg:text-6xl font-secondary-family mb-6 text-white uppercase">
                {{ currentCrew.name }}
              </h2>

              <p class="text-lg font-accent-family text-light-blue leading-relaxed mx-auto lg:mx-0">
                {{ currentCrew.bio }}
              </p>
            </div>

            <!-- Pagination -->
            <nav class="mt-8 lg:mt-0">
              <ul class="flex gap-4 justify-center lg:justify-start">
                <li
                  v-for="member in crew"
                  :key="member.name"
                  class="cursor-pointer h-2 w-2  md:w-4 md:h-4 rounded-full transition-colors"
                  :class="[
                    currentCrew.name === member.name
                      ? 'bg-white'
                      : 'bg-gray-600 hover:bg-gray-400',
                  ]"
                  @click="selectCrew(member)"
                ></li>
              </ul>
            </nav>
          </div>

          <!-- Right (Image) -->
          <div class="w-full lg:w-1/2 flex justify-center items-end">
            <div class="w-64 h-80 md:w-[450px] md:h-[500px] lg:w-full lg:h-[600px] flex items-end justify-center">
              <img
                :src="currentCrew.images?.png"
                :alt="currentCrew.name"
    class="w-full h-full  object-con "
              />
                 <div class="absolute bottom-0 left-0 right-0 h-32 md:h-40 lg:h-48 bg-gradient-to-t from-black/60 via-black/30 to-transparent pointer-events-none"></div>

            </div>
          </div>
          
        </div>
      </div>
    </div>
  </main>
</template>


<script setup>
const crew = [
  {
    name: "Douglas Hurley",
    images: {
      png: "/crew/image-douglas-hurley.png",
      webp: "/crew/image-douglas-hurley.webp",
    },
    role: "Commander",
    bio: "Douglas Gerald Hurley is an American engineer, former Marine Corps pilot and former NASA astronaut. He launched into space for the third time as commander of Crew Dragon Demo-2.",
  },
  {
    name: "Mark Shuttleworth",
    images: {
      png: "/crew/image-mark-shuttleworth.png",
      webp: "/crew/image-mark-shuttleworth.webp",
    },
    role: "Mission Specialist",
    bio: "Mark Richard Shuttleworth is the founder and CEO of Canonical, the company behind the Linux-based Ubuntu operating system. Shuttleworth became the first South African to travel to space as a space tourist.",
  },
  {
    name: "Victor Glover",
    images: {
      png: "/crew/image-victor-glover.png",
      webp: "/crew/image-victor-glover.webp",
    },
    role: "Pilot",
    bio: "Pilot on the first operational flight of the SpaceX Crew Dragon to the International Space Station. Glover is a commander in the U.S. Navy where he pilots an F/A-18.He was a crew member of Expedition 64, and served as a station systems flight engineer.",
  },
  {
    name: "Anousheh Ansari",
    images: {
      png: "/crew/image-anousheh-ansari.png",
      webp: "/crew/image-anousheh-ansari.webp",
    },
    role: "Flight Engineer",
    bio: "Anousheh Ansari is an Iranian American engineer and co-founder of Prodea Systems. Ansari was the fourth self-funded space tourist, the first self-funded woman to fly to the ISS, and the first Iranian in space.",
  },
];

const currentCrew = ref(crew[0]);

const selectCrew = (member) => {
  currentCrew.value = member;
  if (process.client) {
    try {
      sessionStorage.setItem("selectedCrew", JSON.stringify(member));
    } catch (e) {}
  }
};

onMounted(() => {
  if (process.client) {
    try {
      const saved = sessionStorage.getItem("selectedCrew");
      if (saved) {
        const savedCrew = JSON.parse(saved);
        const found = crew.find((m) => m.name === savedCrew.name);
        if (found) {
          currentCrew.value = found;
        }
      }
    } catch (e) {}
  }
});
</script>
