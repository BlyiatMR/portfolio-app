<template>
  <div class="max-w-[1440px] mx-auto my-20">
    <div class="space-y-5">
      <h1 ref="title" class="text-slate-900 text-6xl font-extrabold tracking-wider">
        Hello! I'm <span id="typewriter"></span>
      </h1>
      <h1 ref="subtitle" class="max-w-4xl text-slate-800 text-2xl font-semibold tracking-wider">
        I craft sleek and functional websites that bring ideas to life. Let’s build something extraordinary together.
      </h1>
    </div>
  </div>
</template>

<script setup>
import { ref, onMounted } from "vue";
import gsap from "gsap";
import Typewriter from "typewriter-effect/dist/core";

const title = ref(null);
const subtitle = ref(null);

onMounted(() => {
  const timeline = gsap.timeline();
  timeline
    .from(title.value, {
      opacity: 0,
      y: 50,
      duration: 1.5,
      ease: "power4.out",
    })
    .from(
      subtitle.value,
      {
        opacity: 0,
        y: 50,
        duration: 1.5,
        ease: "power4.out",
      },
      "-=1"
    );

  const typewriter = new Typewriter("#typewriter", {
    loop: true,
    delay: 75,
  });

  typewriter
    .typeString("Hafizh")
    .pauseFor(2000)
    .deleteAll()
    .typeString("Front-end Dev")
    .pauseFor(2000)
    .deleteAll()
    .start();
});
</script>