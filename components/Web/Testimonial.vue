<template>
  <Swiper
    :slides-per-view="1"
    :space-between="50"
    @swiper="onSwiper"
    @slideChange="onSlideChange"
  >
    <SwiperSlide v-for="(data, index) in testimonials" :key="index">
      <WebTestimonials :data="data" :step="activeIndex" />
    </SwiperSlide>
    <div class="image-wrapper">
      <div
        class="img"
        v-for="(data, index) in testimonials"
        :key="index"
        :class="{ active: index === activeIndex }"
      >
        <img :src="data.picture" alt="" />
      </div>
    </div>
  </Swiper>
</template>

<script setup>
import { ref, onMounted } from "vue";
import { Swiper, SwiperSlide } from "swiper/vue";
import "swiper/css";

const testimonials = ref([
  {
    img: "/images/spicy-corner.png",
    testimony:
      "We no longer have to deal with multiple suppliers or chasing people with phone calls to supply us on time. Take take out orders and we expect delivery within 24hours. The service and experience is brilliant.",
    name: "Busayo",
    position: "Co-founder, Spicy Corner",
    picture: "/images/spicycornerceo.png",
  },
  {
    img: "/images/redg.png",
    testimony:
      "GoSource is efficient, cost effective and most importantly their staff are always ready to proffer solutions to the regular issues Lagos will present you with. As a small business owner this is invaluable.",
    name: "Seun Adebajo",
    position: "Co-founder, Red Gourmet Kitchen",
    picture: "/images/redceo.png",
  },
  {
    img: "/images/citysub.png",
    testimony:
      "GoSource has shown they love my business and it’s clear from the way they operate. They also provide the logistics service we use daily. It has given us time to focus on selling great food to our customers.",
    name: "Demi Odunubi",
    position: "Co-founder, City Subs",
    picture: "/images/citysubceo.png",
  },
]);
const activeIndex = ref(0);
const swiperInstance = ref(null);
const textContent = ref("");

const onSwiper = (swiper) => {
  swiperInstance.value = swiper;
  activeIndex.value = swiperInstance.value.activeIndex;
};

const onSlideChange = () => {
  activeIndex.value = swiperInstance.value.activeIndex;
  // step.value++
};

onMounted(() => {});
</script>

<style scoped>
.image-wrapper {
  display: flex;
  align-items: center;
  gap: 12px;
  justify-content: center;
  margin-top: 32px;
}

.img {
  opacity: 0.4;
  width: 32px;
  height: 32px;
  transition: all calc(var(--animation-duration) * 0.2);
}

.img.active {
  opacity: 1;
  width: 44px;
  height: 44px;
}
</style>
