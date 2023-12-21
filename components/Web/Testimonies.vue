<template>
  <Swiper
    :slides-per-view="1"
    :space-between="50"
    @swiper="onSwiper"
    @slideChange="onSlideChange"
  >
    <SwiperSlide v-for="(data, index) in data" :key="index">
      <div class="wrapper">
        <div class="brand">
          <img :src="data.img" alt="" />
        </div>
        <div class="testimony base-font">
          <span
            v-for="(letter, index) in lettersArray"
            :key="index"
            :style="{ color: letter.color }"
          >
            {{ letter.value }}
          </span>
        </div>
        <div class="name">
          <h5 class="heading-5-medium medium text-grey-900-base">{{ data.name }}</h5>
          <p class="body-small-regular regular text-grey-500">{{ data.position }}</p>
        </div>
      </div>
    </SwiperSlide>
  </Swiper>
</template>

<script setup>
import { ref, onMounted, watchEffect } from "vue";
import { Swiper, SwiperSlide } from "swiper/vue";
import "swiper/css";

const { data } = defineProps({
  data: {
    type: Array,
    required: true,
  },
});

const step = ref(0);
const activeIndex = ref(0);
const swiperInstance = ref(null);
const lettersArray = ref([]);
const snippet = data[step.value].testimony;

const hello = () => {};

watchEffect(async () => {
  hello();
});

const onSwiper = (swiper) => {
  swiperInstance.value = swiper;
  activeIndex.value = swiperInstance.value.activeIndex;
  console.log(snippet);
};

const splitTextIntoLetters = () => {
  const text = snippet;
  const textArray = text.split("");

  lettersArray.value = textArray.map((letter, index) => ({
    value: letter,
    color: "var(--grey-500)", // Initial color, you can adjust this
  }));

  animateText();
};

function resetColors() {
  lettersArray.value.forEach((letter) => {
    letter.color = "var(--grey-500)";
  });
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

const onSlideChange = () => {
  activeIndex.value = swiperInstance.value.activeIndex;
  step.value++;
  console.log(snippet);
  // step.value++
};

onMounted(() => {
  console.log(swiperInstance.value);
  splitTextIntoLetters();
});
</script>

<style scoped>
.wrapper {
  display: flex;
  /* max-width: 1140px; */
  margin-inline: auto;
  width: 100%;
  flex-direction: column;
  align-items: center;
  gap: 48px;
}

.name {
  display: flex;
  flex-direction: column;
  align-items: center;
  gap: 2px;
}

.testimony {
  max-width: 823px;
  width: 100%;
  text-align: center;
  font-size: 34px;
  font-style: normal;
  font-weight: 500;
  line-height: 51px; /* 150% */
  letter-spacing: -1px;
  transition: all 0.2s ease;
}
@media (max-width: 960px) {
  .testimony {
    font-size: 20px;
    font-weight: 500;
    line-height: 30px; /* 150% */
    letter-spacing: -0.3px;
  }
}
</style>
