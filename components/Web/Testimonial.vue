<template>
  <swiper
    :slides-per-view="1"
    :space-between="10"
    @swiper="onSwiper"
    @slideChange="onSlideChange"
  >
    <swiper-slide v-for="(data, index) in testimonials" :key="index">
      <WebTestimonials :data="data" />
    </swiper-slide>
    <!-- ... other slides -->
  </swiper>
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
  },
  {
    img: "/images/spicy-corner.png",
    testimony:
      "GoSource is efficient, cost effective and most importantly their staff are always ready to proffer solutions to the regular issues Lagos will present you with. As a small business owner this is invaluable.",
    name: "Seun Adebajo",
    position: "Co-founder, Red Gourmet Kitchen",
  },
  {
    img: "/images/spicy-corner.png",
    testimony:
      "GoSource has shown they love my business and it’s clear from the way they operate. They also provide the logistics service we use daily. It has given us time to focus on selling great food to our customers.",
    name: "Demi Odunubi",
    position: "Co-founder, City Subs",
  },
]);

const onSwiper = (swiper) => {
  // console.log(swiper);
};

const onSlideChange = () => {
  // console.log("slide change");
};

// Assuming you need to use Swiper's methods or properties
const swiperInstance = ref(null);

onMounted(() => {
  // Access Swiper instance using the ref
  console.log(swiperInstance.value);
});
</script>
