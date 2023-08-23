<script setup>
import { RouterLink } from 'vue-router'
</script>

<template>
  <section>
    <div class="content">
      <h2 class="uppercase">So, you want to travel to</h2>
      <h1 class="space uppercase">Space</h1>
      <p>
        Let’s face it; if you want to go to space, you might as well genuinely go to outer space and
        not hover kind of on the edge of it. Well sit back, and relax because we’ll give you a truly
        out of this world experience!
      </p>
    </div>
    <RouterLink to="/destination" class="explore-link"
      ><div class="explore"><h1 class="uppercase">Explore</h1></div></RouterLink
    >
  </section>
</template>

<style scoped>
section {
  justify-content: space-between;
  align-items: end;
  padding-top: 8rem;
}

.content {
  display: flex;
  flex-direction: column;
  gap: 2rem;
}

div {
  width: 40%;
}

h1.space {
  font-size: clamp(5rem, 8vw + 1rem, 9.375rem);
  line-height: 1.1;
}

.explore h1 {
  letter-spacing: 1px;
  font-size: 2rem;
}

.explore {
  display: flex;
  justify-content: center;
  align-items: center;
  align-self: center;
  width: 300px;
  height: 300px;
  background-color: white;
  color: black;
  border-radius: 50%;
  margin-top: 6rem;
  transition: all 1s ease-in-out;
}

.explore:hover {
  scale: 1.3;
  opacity: 0.5;
  cursor: pointer;
}

@media (max-width: 1024px) {
  section {
    flex-direction: column;
    padding-top: 5rem;
  }

  h1.space {
    font-size: clamp(15rem, 14vw + 1rem, 9.375rem);
  }
  .content {
    text-align: center;
    width: 100%;
    margin: 0 auto;
  }

  h2 {
    font-size: 1.5rem;
    font-family: var(--main-font);
  }

  p {
    line-height: 2;
    width: 70%;
    margin: 0 auto;
  }
  .explore-link {
    margin: 0 auto;
  }
}

@media (max-width: 768px) {
  h1.space {
    font-size: clamp(5rem, 4vw + 1rem, 9.375rem);
  }

  h2 {
    font-size: 0.9rem;
  }
}
</style>
