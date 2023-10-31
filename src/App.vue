<script setup>
import { ref } from 'vue'
import { RouterLink, RouterView } from 'vue-router'

let media = ref('desktop')
let nav = ref(false)



function getImg(name) {
  let imageUrl = new URL(`./assets/${name}/background-${name}-${media.value}.jpg`, import.meta.url)
    .href
  return imageUrl
}

function openNav(){
  nav.value = true
}

function closeNav(){
  nav.value = false
}


</script>

<template>
  <main
    :style="{
      'background-image':
        'url(' + getImg($route.fullPath === '/' ? 'home' : $route.fullPath.substring(1)) + ')'
    }"
  >
    <header>
      <img src="./assets/shared/logo.svg" alt="logo" class="logo" />

      <div class="hr"></div>
      
      <img
        src="./assets/shared/icon-hamburger.svg"
        alt="burger"
        class="burger nav-icon"
        @click="openNav"
        v-show="!nav"
        />
        <img src="./assets/shared/icon-close.svg" alt="" class="close nav-icon" @click="closeNav" v-show="nav"/>
        <nav id="desktop-nav" v-show="nav">
          <RouterLink to="/">
            00 <span>Home</span></RouterLink
          >
          <RouterLink to="/destination">
            01 <span>Destination</span></RouterLink
          >
          <RouterLink to="crew"
            >02 <span>Crew</span></RouterLink
          >
          <RouterLink to="technology"
            >03 <span>Technology</span></RouterLink
          >
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
  box-sizing: border-box;
}

body {
  background-color: rgb(15, 15, 15);
  font-family: var(--main-font);
}

main {
  min-height: 100vh;
  background-size: cover;
  background-repeat: no-repeat;
  transition: all 0.5s ease-in-out;
  color: white;
}

section {
  display: flex;
}

.container {
  margin: 0 auto;
  padding: 0 1rem;
}

@media (min-width: 576px) {
  .container {
    max-width: 540px;
  }
}

@media (min-width: 768px) {
  .container {
    max-width: 720px;
  }
}

@media (min-width: 992px) {
  .container {
    max-width: 960px;
  }
}

@media (min-width: 1200px) {
  .container {
    max-width: 1140px;
  }
}

h1,
h2,
h3,
h4,
h5,
h6 {
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

.hide {
  display: none;
}

a{
  all: unset;
}

.hr {
  height: 1px;
  width: 40%;
  background-color: rgb(230 238 254 / 32%);
}

header {
  width: 100%;
  display: flex;
  justify-content: space-between;
  align-items: center;
  margin: 0 auto;
  padding-top: 2rem;
}

header .logo {
  padding: 2rem 3rem;
}

nav {
  background: rgba(83, 101, 136, 0.32);
  backdrop-filter: blur(3px);
  -webkit-backdrop-filter: blur(3px);
  padding: 0 4rem;
  display: flex;
  gap: 3rem;
}

.nav-icon{
  position: absolute;
  top: 3rem;
  right: 2rem;
  width: 30px;
  z-index: 2;
    &:hover{
      cursor: pointer;
    }
}

nav a{
  white-space: nowrap;
  font-family: var(--main-font);
  text-transform: uppercase;
  letter-spacing: 2.75px;
  padding:2rem 0;
  &:hover{
    cursor: pointer;
  }
}

a > span{
  color: var(--dark-color);
}

.router-link-active {
  border-bottom: 2px solid white;
}
@media (max-width:1024px) {
  nav{
    padding:2rem 1rem ;
    width: 70%;
    background: rgba(83, 101, 136, 0.8);
    flex-direction: column;
    position: absolute;
    top: 0  ;
    right: 0;
    padding-left: 2rem;
    align-items: start;
    z-index: 1;
    a{
      &:hover{
        padding-left: 1rem;
      }

    }
  }
  .burger{
    display: block;
  }
  .hr{
    display: none;
  }
}

@media (width > 1024px) {
  .burger,.close{
    display: none;
  }
}

@media (max-width: 768px) {
  .container {
    width: 90%;
    margin: 0 auto;
  }
  
  h2 {
    font-size: 0.8rem;
  }
  h3{
    font-size: 0.7rem;
    white-space: wrap;
  }
  h4{
    font-size: 0.6rem;
  }
  p {
    font-size: 0.9rem;
  }
  header nav{
    padding:0 1.5rem;
  }
  .nav-icon{
    right: 1rem;
    width: 20px;
  }
}


</style>
