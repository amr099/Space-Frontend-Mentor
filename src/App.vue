<script setup>
import { ref } from 'vue'
import { RouterLink, RouterView } from 'vue-router'

let media = ref('desktop')
let showNav = ref(false)

window.addEventListener('resize', () => {
  let m = window.innerWidth
  if (m <= 1024 && m > 769) {
    media.value = 'tablet'
    closeNav()
  } else if (m <= 769) {
    media.value = 'mobile'
  } else {
    media.value = 'desktop'
    closeNav()
  }
})

function getImg(name) {
  let imageUrl = new URL(`./assets/${name}/background-${name}-${media.value}.jpg`, import.meta.url)
    .href
  return imageUrl
}

function closeNav() {
  showNav.value = false
}
function openNav() {
  showNav.value = true
}
</script>

<template>
  <main
    :style="{
      'background-image':
        'url(' + getImg($route.fullPath != '/' ? $route.fullPath.substring(1) : 'home') + ')'
    }"
  >
    <header>
      <img src="./assets/shared/logo.svg" alt="logo" />
      <img
        src="./assets/shared/icon-hamburger.svg"
        alt="hamburger"
        :class="{ hide: media != 'mobile' }"
        @click="openNav"
      />
      <nav :class="{ hide: !showNav }" id="mobile-nav">
        <ul>
          <li class="close" @click="closeNav">
            <img src="./assets/shared/icon-close.svg" alt="" />
          </li>
          <RouterLink to="/">
            <li>00 <span>Home</span></li></RouterLink
          >
          <RouterLink to="/destination">
            <li>01 <span>Destination</span></li></RouterLink
          >
          <RouterLink to="crew"
            ><li>02 <span>Crew</span></li></RouterLink
          >
          <RouterLink to="technology"
            ><li>03 <span>Technology</span></li></RouterLink
          >
        </ul>
      </nav>
      <nav :class="{ hide: media === 'mobile' }" id="desktop-nav">
        <ul>
          <RouterLink to="/">
            <li>00 <span>Home</span></li></RouterLink
          >
          <RouterLink to="/destination">
            <li>01 <span>Destination</span></li></RouterLink
          >
          <RouterLink to="crew"
            ><li>02 <span>Crew</span></li></RouterLink
          >
          <RouterLink to="technology"
            ><li>03 <span>Technology</span></li></RouterLink
          >
        </ul>
      </nav>
    </header>
    <div class="container">
      <RouterView />
    </div>
  </main>
</template>

<style>
@font-face {
  font-family: Bellefair;
  src: url(./assets/fonts/Bellefair-Regular.ttf);
}
@font-face {
  font-family: BarlowCondensed;
  src: url(./assets/fonts/BarlowCondensed-Regular.ttf);
}
:root {
  --dark-color: #d2d8f9;
  --main-font: 'BarlowCondensed';
  --second-font: 'Bellefair', 'serifs';
}

* {
  margin: 0;
  padding: 0;
}

body {
  font-family: var(--main-font);
}

main {
  background-repeat: no-repeat;
  background-size: cover;
  transition: all 0.5s ease-in-out;
  color: white;
  min-height: 100vh;
}

section {
  display: flex;
}

h1,
h2,
h3,
h4,
h5,
h6 {
  white-space: nowrap;
  text-transform: uppercase;
}

h1 {
  font-family: var(--second-font);
  font-weight: 100;
}

h2 {
  font-size: 1.75rem;
  font-family: var(--second-font);
  color: var(--dark-color);
  letter-spacing: 4.75px;
  font-weight: 100;
}

h3 {
  font-family: var(--second-font);
  letter-spacing: 2.75px;
  font-size: 1.75rem;
  font-weight: 100;
  text-transform: uppercase;
  display: flex;
  gap: 1rem;
  align-items: center;
  padding-top: 2rem;
}

h3 span {
  font-family: var(--main-font);
  color: rgb(85, 85, 85);
  font-size: 1.75rem;
  text-transform: uppercase;
  font-weight: bold;
}

p {
  color: var(--dark-color);
  line-height: 1.5;
  font-size: 1.4rem;
}

.hr {
  height: 1px;
  width: 40%;
  background-color: rgb(230 238 254 / 32%);
  position: relative;
  left: 3rem;
}

.container {
  width: 70%;
  margin: 0 auto;
}

header {
  width: 100%;
  display: flex;
  justify-content: space-between;
  align-items: center;
  margin: 0 auto;
  padding-top: 2rem;
}

header img {
  width: 50px;
  padding: 2rem 3rem;
}

header nav#desktop-nav {
  width: 50%;
  background: rgba(83, 101, 136, 0.32);
  backdrop-filter: blur(1px);
  -webkit-backdrop-filter: blur(7px);
  padding: 0 4rem;
}

header nav {
  width: 50%;
  background: rgba(83, 101, 136, 0.32);
  backdrop-filter: blur(1px);
  -webkit-backdrop-filter: blur(7px);
  padding: 0 4rem;
}

ul {
  display: flex;
  gap: 3rem;
  list-style: none;
  margin: 0;
  padding: 0 0 0 1rem;
}

nav#mobile-nav {
  z-index: 200;
  width: 100%;
  padding: 3rem 0;
  text-align: center;
  background-color: rgb(27, 27, 27, 0.8);
  position: absolute;
  top: 0;
  right: 0;
}

nav#mobile-nav ul {
  width: 100%;
  flex-direction: column;
  justify-content: center;
  align-items: center;
}
nav#mobile-nav li {
  font-size: 2rem;
}

.close {
  align-self: start;
  width: 30px;
  padding: 0;
}

header ul {
  width: 40%;
}
header li {
  padding: 2rem 0 2rem;
}

li {
  white-space: nowrap;
  font-family: var(--main-font);
  text-transform: uppercase;
  font-size: 1rem;
  letter-spacing: 2.75px;
}

li:hover {
  /* border-bottom: 2px solid var(--secend-color); */
  cursor: pointer;
}

li span {
  color: var(--dark-color);
}

a {
  all: unset;
}

.hide {
  display: none;
}

.router-link-active {
  border-bottom: 2px solid white;
}

@media (max-width: 768px) {
  .container {
    width: 90%;
    margin: 0 auto;
  }

  h3 {
    font-size: 1rem;
    text-align: center;
  }
  p {
    font-size: 0.9rem;
  }
}
</style>
