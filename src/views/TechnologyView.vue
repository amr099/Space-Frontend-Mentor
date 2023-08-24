<script setup>
import { ref } from 'vue'
const data = [
  {
    name: 'Launch vehicle',
    images: {
      portrait: '../assets/technology/image-launch-vehicle-portrait.jpg',
      landscape: '../assets/technology/image-launch-vehicle-landscape.jpg'
    },
    description:
      "A launch vehicle or carrier rocket is a rocket-propelled vehicle used to carry a payload from Earth's surface to space, usually to Earth orbit or beyond. Our WEB-X carrier rocket is the most powerful in operation. Standing 150 metres tall, it's quite an awe-inspiring sight on the launch pad!"
  },
  {
    name: 'Spaceport',
    images: {
      portrait: '../assets/technology/image-spaceport-portrait.jpg',
      landscape: '../assets/technology/image-spaceport-landscape.jpg'
    },
    description:
      'A spaceport or cosmodrome is a site for launching (or receiving) spacecraft, by analogy to the seaport for ships or airport for aircraft. Based in the famous Cape Canaveral, our spaceport is ideally situated to take advantage of the Earth’s rotation for launch.'
  },
  {
    name: 'Space capsule',
    images: {
      portrait: '../assets/technology/image-space-capsule-portrait.jpg',
      landscape: '../assets/technology/image-space-capsule-landscape.jpg'
    },
    description:
      "A space capsule is an often-crewed spacecraft that uses a blunt-body reentry capsule to reenter the Earth's atmosphere without wings. Our capsule is where you'll spend your time during the flight. It includes a space gym, cinema, and plenty of other activities to keep you entertained."
  }
]

function getImg(path) {
  let imageUrl = new URL(path, import.meta.url).href
  return imageUrl
}

const index = ref(0)

function load(i) {
  index.value = i
}
</script>
<template>
  <h3><span>03</span> Space Launch 101</h3>
  <section>
    <nav>
      <div :class="{ selected: index === 0 }" @click="load(0)">1</div>
      <div :class="{ selected: index === 1 }" @click="load(1)">2</div>
      <div :class="{ selected: index === 2 }" @click="load(2)">3</div>
    </nav>
    <div class="content">
      <h5>The Technology...</h5>
      <h1>{{ data[index].name }}</h1>
      <p>
        {{ data[index].description }}
      </p>
    </div>
    <div
      class="img"
      :style="{ 'background-image': 'url(' + getImg(data[index].images.portrait) + ')' }"
      :key="data[index].images.portrait"
    ></div>
  </section>
</template>
<style scoped>
section {
  color: white;
  gap: 2rem;
  margin-top: 10rem;
}

nav {
  display: flex;
  flex-direction: column;
  gap: 2rem;
}

h5 {
  font-size: 1rem;
  margin-bottom: 2rem;
  font-family: var(--second-font);
  color: var(--second-color);
  letter-spacing: 2.75px;
}

h1 {
  font-size: 3rem;
  margin-bottom: 2rem;
  color: var(--dark-color);
  letter-spacing: 2.75px;
}
nav > div {
  width: 70px;
  height: 70px;
  border-radius: 50%;
  background-color: transparent;
  border: 1px solid var(--dark-color);
  display: flex;
  justify-content: center;
  align-items: center;
  font-size: 2rem;
}

nav > div:hover {
  cursor: pointer;
}
.content {
  width: 50%;
}

.img {
  width: 30%;
  height: 60vh;
  background-size: contain;
  background-repeat: no-repeat;
  transition: all 0.5s ease-in-out;
  position: absolute;
  bottom: 0;
  right: 0;
}

.selected {
  background-color: white;
  color: black;
}

@media (max-width: 1024px) {
  section {
    flex-direction: column-reverse;
  }

  nav {
    order: 1;
    flex-direction: row;
    justify-content: space-around;
  }

  .content {
    text-align: center;
    width: 90%;
    margin: 0 auto;
  }

  .img {
    position: static;
    order: 1;
    width: 100%;
    height: 100vh;
    background-size: cover;
  }
}

@media (max-width: 769px) {
  .img {
    height: 40vh;
  }

  h1 {
    font-size: 2rem;
  }
}
</style>
