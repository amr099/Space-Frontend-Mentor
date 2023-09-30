<script steup>
const props = defineProps({ media: Boolean })
</script>
<template>
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
</template>
<style scoped>
nav {
  width: 50%;
  background: rgba(83, 101, 136, 0.32);
  backdrop-filter: blur(5px);
  -webkit-backdrop-filter: blur(5px);
  padding: 0 4rem;
}
</style>
