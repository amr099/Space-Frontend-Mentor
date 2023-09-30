<script setup>
import { ref } from 'vue'
const data = [
  {
    name: 'Douglas Hurley',
    images: {
      png: '../assets/crew/image-douglas-hurley.png',
      webp: '../assets/crew/image-douglas-hurley.webp'
    },
    role: 'Commander',
    bio: 'Douglas Gerald Hurley is an American engineer, former Marine Corps pilot and former NASA astronaut. He launched into space for the third time as commander of Crew Dragon Demo-2.'
  },
  {
    name: 'Mark Shuttleworth',
    images: {
      png: '../assets/crew/image-mark-shuttleworth.png',
      webp: '../assets/crew/image-mark-shuttleworth.webp'
    },
    role: 'Mission Specialist',
    bio: 'Mark Richard Shuttleworth is the founder and CEO of Canonical, the company behind the Linux-based Ubuntu operating system. Shuttleworth became the first South African to travel to space as a space tourist.'
  },
  {
    name: 'Victor Glover',
    images: {
      png: '../assets/crew/image-victor-glover.png',
      webp: '../assets/crew/image-victor-glover.webp'
    },
    role: 'Pilot',
    bio: 'Pilot on the first operational flight of the SpaceX Crew Dragon to the International Space Station. Glover is a commander in the U.S. Navy where he pilots an F/A-18.He was a crew member of Expedition 64, and served as a station systems flight engineer.'
  },
  {
    name: 'Anousheh Ansari',
    images: {
      png: '../assets/crew/image-anousheh-ansari.png',
      webp: '../assets/crew/image-anousheh-ansari.webp'
    },
    role: 'Flight Engineer',
    bio: 'Anousheh Ansari is an Iranian American engineer and co-founder of Prodea Systems. Ansari was the fourth self-funded space tourist, the first self-funded woman to fly to the ISS, and the first Iranian in space.'
  }
]
const index = ref(0)

function getImg(path) {
  let imageUrl = new URL(path, import.meta.url).href
  return imageUrl
}

function load(i) {
  index.value = i
}
</script>
<template>
  <h3><span>02</span> Meet your crew</h3>
  <section>
    <div class="content">
      <div class="info">
        <h2>{{ data[index].role }}</h2>
        <h1>{{ data[index].name }}</h1>
        <p>
          {{ data[index].bio }}
        </p>
      </div>
      <nav>
        <div :class="{ selected: index === 0 }" @click="load(0)"></div>
        <div :class="{ selected: index === 1 }" @click="load(1)"></div>
        <div :class="{ selected: index === 2 }" @click="load(2)"></div>
        <div :class="{ selected: index === 3 }" @click="load(3)"></div>
      </nav>
    </div>
    <div
      class="img"
      :style="{ 'background-image': 'url(' + getImg(data[index].images.png) + ')' }"
      :key="data[index].images.png"
    ></div>
  </section>
</template>
<style scoped>
section {
  color: white;
  justify-content: space-between;
}

h1 {
  font-size: 3rem;
}

p {
  font-size: 1.2rem;
}

nav {
  display: flex;
  gap: 2rem;
  justify-self: flex-end;
}

.content {
  width: 40%;
  padding-top: 5rem;
  display: flex;
  flex-direction: column;
  gap: 6rem;
}

.info {
  display: flex;
  flex-direction: column;
  gap: 2rem;
}

.img {
  width: 40%;
  height: 70vh;
  background-size: contain;
  background-repeat: no-repeat;
  transition: all 0.5s ease-in-out;
  position: absolute;
  bottom: 0;
  right: 0;
}

nav > div {
  width: 20px;
  height: 20px;
  border-radius: 50%;
  background-color: white;
  opacity: 0.2;
  transition: all 0.5s ease-in-out;
}

nav > div:hover {
  cursor: pointer;
}

.selected {
  opacity: 1;
  scale: 1.3;
}

@media (max-width: 1024px) {
  section {
    flex-direction: column;
    justify-content: center;
    gap: 3rem;
  }
  .content {
    width: 100%;
    margin: 0 auto;
    text-align: center;
    justify-content: center;
  }
  nav {
    justify-content: center;
  }
  .img {
    position: relative;
    width: 70%;
    margin: 0 auto;
    background-size: cover;
  }
}

@media (max-width: 769px) {
  section {
    flex-direction: column-reverse;
    justify-content: center;
  }

  .content {
    flex-direction: column-reverse;
    padding-top: 0px;
  }

  h1 {
    font-size: 1.7rem;
  }
  h2 {
    font-size: 1rem;
    letter-spacing: 0px;
  }
  p {
    font-size: 0.8;
  }
  .img {
    width: 100%;
    margin-top: 2rem;
    background-size: contain;
  }
}
</style>
