<script steup>
import { RouterLink, RouterView } from 'vue-router'
const props = defineProps({ mobNav: Boolean, media: String, closeNav: Function })
</script>
<template>
  <nav :class="{ hide: !mobNav }" id="mobile-nav">
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
</template>
<style scoped>
nav {
  z-index: 200;
  width: 100%;
  padding: 3rem 0;
  text-align: center;
  background-color: rgb(27, 27, 27, 0.8);
  position: absolute;
  top: 0;
  right: 0;
}
</style>
