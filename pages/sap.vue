<template>
  <div>
    <section>
      <h1>Scroll down for awesomeness.</h1>
    </section>

    <section>
      <p
        ref="revealType"
        class="reveal-type"
        data-bg-color="#cccccc"
        data-fg-color="teal"
      >
        Systematically ushering in a new generation of amazing designers from across the
        globe.
      </p>
    </section>

    <section>
      <p
        ref="revealType"
        class="reveal-type"
        data-bg-color="#b6b600"
        data-fg-color="black"
      >
        Modern UI designers will expand their skillsets to include frontend.
      </p>
    </section>

    <section>
      <p ref="revealType" class="reveal-type" data-bg-color="#353535" data-fg-color="red">
        The web isn't static anymore, interactivity and motion now dominate.
      </p>
    </section>

    <section></section>
  </div>
</template>

<script setup>
import { onMounted } from "vue";
import { gsap } from "gsap";
import { ScrollTrigger } from "gsap/ScrollTrigger";
import SplitType from "split-type";
import Lenis from '@studio-freight/lenis'

gsap.registerPlugin(ScrollTrigger);

onMounted(() => {
  const splitTypes = document.querySelectorAll(".reveal-type");

  splitTypes.forEach((char, i) => {
    const bg = char.dataset.bgColor;
    const fg = char.dataset.fgColor;

    const text = new SplitType(char, { types: "chars" });

    gsap.fromTo(
      text.chars,
      {
        color: bg,
      },
      {
        color: fg,
        duration: 1,
        stagger: 0.02,
        scrollTrigger: {
          trigger: char,
          start: "top 80%",
          end: "top 20%",
          scrub: true,
          markers: false,
          toggleActions: "play play reverse reverse",
        },
      }
    );
  });

  const lenis = new Lenis();

  lenis.on("scroll", (e) => {
    console.log(e);
  });

  function raf(time) {
    lenis.raf(time);
    requestAnimationFrame(raf);
  }

  requestAnimationFrame(raf);
});
</script>

<style scoped>
body {
  margin: 0;
  font-family: sans-serif;
}

section {
  height: 100vh;
  padding: clamp(4rem, 12vh, 20rem);
  display: grid;
  place-content: center;
}

section p {
  font-size: clamp(2rem, 5vw, 8rem);
}

section:nth-of-type(1) {
  border-bottom: 1px solid black;
}

section:nth-of-type(3) {
  background: #ffff00;
}

section:nth-of-type(4) {
  background: rgb(29, 29, 29);
  color: white;
}
</style>
