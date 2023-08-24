<script setup>
import { ref } from 'vue'

const data = [
  {
    name: 'Moon',
    images: {
      png: '../assets/destination/image-moon.png',
      webp: '../assets/destination/image-moon.webp'
    },
    description:
      'See our planet as you’ve never seen it before. A perfect relaxing trip away to help regain perspective and come back refreshed. While you’re there, take in some history by visiting the Luna 2 and Apollo 11 landing sites.',
    distance: '384,400 km',
    travel: '3 days'
  },
  {
    name: 'Mars',
    images: {
      png: '../assets/destination/image-mars.png',
      webp: '../assets/destination/image-mars.webp'
    },
    description:
      'Don’t forget to pack your hiking boots. You’ll need them to tackle Olympus Mons, the tallest planetary mountain in our solar system. It’s two and a half times the size of Everest!',
    distance: '225 mil. km',
    travel: '9 months'
  },
  {
    name: 'Europa',
    images: {
      png: '../assets/destination/image-europa.png',
      webp: '../assets/destination/image-europa.webp'
    },
    description:
      'The smallest of the four Galilean moons orbiting Jupiter, Europa is a winter lover’s dream. With an icy surface, it’s perfect for a bit of ice skating, curling, hockey, or simple relaxation in your snug wintery cabin.',
    distance: '628 mil. km',
    travel: '3 years'
  },
  {
    name: 'Titan',
    png: '../assets/destination/image-titan.png',
    images: {
      png: '../assets/destination/image-titan.png',
      webp: '../assets/destination/image-titan.webp'
    },
    description:
      'The only moon known to have a dense atmosphere other than Earth, Titan is a home away from home (just a few hundred degrees colder!). As a bonus, you get striking views of the Rings of Saturn.',
    distance: '1.6 bil. km',
    travel: '7 years'
  }
]

function getImg(path) {
  let imageUrl = new URL(path, import.meta.url).href
  console.log(imageUrl)
  return imageUrl
}

const planetData = ref(data[0])

function load(i) {
  planetData.value = data[i]
}
</script>
<template>
  <section>
    <h3><span>01</span> Pick your destination</h3>
    <div class="content">
      <div
        class="img"
        :style="{ 'background-image': 'url(' + getImg(planetData?.images.png) + ')' }"
        :key="planetData?.images.png"
      ></div>
      <div class="details">
        <nav>
          <ul>
            <li @click="load(0)" :class="{ selected: planetData.name === 'Moon' }">Moon</li>
            <li @click="load(1)" :class="{ selected: planetData.name === 'Mars' }">Mars</li>
            <li @click="load(2)" :class="{ selected: planetData.name === 'Europa' }">Europa</li>
            <li @click="load(3)" :class="{ selected: planetData.name === 'Titan' }">Titan</li>
          </ul>
        </nav>
        <h1>{{ planetData?.name }}</h1>
        <p>
          {{ planetData?.description }}
        </p>
        <hr />
        <div class="info">
          <div>
            <h4>AVG. DISTANCE</h4>
            <h2>{{ planetData?.distance }}</h2>
          </div>
          <div>
            <h4>EST. TRAVEL TIME</h4>
            <h2>{{ planetData?.travel }}</h2>
          </div>
        </div>
      </div>
    </div>
  </section>
</template>
<style scoped>
h1 {
  font-size: 4rem;
}
p {
  padding-bottom: 3rem;
}
section {
  flex-direction: column;
  gap: 3rem;
}
.content {
  display: flex;
  justify-content: space-around;
  align-items: center;
}

.img {
  width: 40%;
  height: 50vh;
  background-size: contain;
  background-repeat: no-repeat;
  transition: all 0.5s ease-in-out;
}

.details {
  width: 40%;
}

ul {
  padding: 0;
  padding-bottom: 3rem;
}

li {
  font-size: 1rem;
  letter-spacing: 2px;
  font-family: var(--second-font);
  font-weight: 100;
}

h4 {
  font-size: 0.8rem;
}

h2,
h4 {
  margin: 1rem 0;
  letter-spacing: 2px;
  font-family: var(--second-font);
  font-weight: 100;
}
.info {
  display: flex;
  justify-content: space-between;
}

.selected {
  border-bottom: 1px solid white;
}

@media (max-width: 1024px) {
  .content {
    flex-direction: column;
    text-align: center;
    padding-top: 7rem;
    width: 100%;
    margin: 0 auto;
    padding-top: 1rem;
  }
  .img {
    width: 50%;
    height: 50vh;
    margin: 0 auto;
  }

  .details {
    display: flex;
    flex-direction: column;
    gap: 2rem;
    width: 80%;
  }

  .details nav {
    display: flex;
    justify-content: space-around;
  }
  h2,
  h4 {
    text-align: left;
  }
}

@media (max-width: 769px) {
  .content {
    padding-top: 2rem;
  }

  .details {
    width: 100%;
  }

  .img {
    width: 70%;
    height: 40vh;
  }

  li {
    font-size: 0.7rem;
  }

  h2,
  h4 {
    font-size: 0.7rem;
  }
}
</style>
