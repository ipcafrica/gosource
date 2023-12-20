<template>
  <div>
    <WebTestimonial />
    <p ref="text" class="animated-text">
      <span v-for="(letter, index) in lettersArray" :key="index" :style="{ color: letter.color }">
        {{ letter.value }}
      </span>
    </p>
  </div>
</template>

<script setup>
import { ref, onMounted } from "vue";

const snippet = ref(
  "We no longer have to deal with multiple suppliers or chasing people with phone calls to supply us on time. Take take out orders and we expect delivery within 24 hours. The service and experience is brilliant."
);

const lettersArray = ref([]);

onMounted(() => {
  splitTextIntoLetters();
});

const splitTextIntoLetters = () => {
  const text = snippet.value;
  const textArray = text.split("");

  lettersArray.value = textArray.map((letter, index) => ({
    value: letter,
    color: "var(--grey-500)", // Initial color, you can adjust this
  }));

  animateText();
}

function animateText() {
  let index = 0;

  function updateColor() {
    lettersArray.value[index].color = "var(--grey-900-base)";
  }

  function animate() {
    if (index < lettersArray.value.length) {
      updateColor();
      index++;
      setTimeout(animate, 100); // Adjust the delay as needed
    }
  }

  animate();
}
</script>

<style scoped>
.animated-text span {
  font-size: 48px;
  transition: all 0.2s ease;
}
</style>
