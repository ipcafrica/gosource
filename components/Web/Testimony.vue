<template>
  <div class="testimonial-slider">
    <div class="testimonial-container">
      <div class="testimonials" :style="{ transform: `translateX(${-currentIndex * 100}%)` }">
        <div class="testimonial" v-for="(user, index) in users" :key="index"
          :class="{ displayed: currentIndex === index }">
          <img :src="user.logo" />
          <p class="user-testimony">
            {{ user.testimony }} <span class="new text-grey-500">{{ user.continue }}</span>
          </p>
          <div class="details">
            <p class="text-heading-5-medium medium text-grey-900-base">{{ user.name }}</p>
            <span class="text-body-small-regular regular text-grey-700">{{ user.post }}</span>
          </div>
        </div>
      </div>

      <div class="pagination-dots">
        <div class="user-image" v-for="(user, index) in users" :key="index" :class="{ active: currentIndex === index }">
          <img :src="user.image" @mouseover="pauseAutoSlide" @mouseleave="resumeAutoSlide" @click="goToIndex(index)" />
        </div>
      </div>
    </div>
  </div>
</template>

<script setup>
import { ref, onMounted, onUnmounted } from 'vue';

const users = ref([
  {
    testimony:
      "We no longer have to deal with multiple suppliers or chasing people with",
    continue:
      "phone calls to supply us on time. Take take out orders and we expect delivery within 24hours. The service and experience is brilliant.",
    name: "Busayo",
    post: "co-founder, spicy corner",
    logo: "/spicy.svg",
    image: "/one.svg",
  },
  {
    testimony:
      "GoSource is efficient, cost effective and most importantly their staff are",
    continue:
      "always ready to proffer solutions to the regular issues Lagos will present you with. As a small business owner this is invaluable.",
    name: "Seun Adebajo",
    post: "Co-founder, Red Gourmet Kitchen",
    logo: "/red.svg",
    image: "/two.svg",
  },
  {
    testimony:
      "GoSource has shown they love my business and it’s clear from the way",
    continue:
      "they operate. They also provide the logistics service we use daily. It has given us time to focus on selling great food to our customers.",
    name: "Demi Odunubi",
    post: "Co-founder, City Subs",
    logo: "/subs.svg",
    image: "/three.svg",
  },
]);
const currentIndex = ref(0);
let interval;

const goToIndex = (index) => {
  currentIndex.value = index;
};

const nextSlide = () => {
  currentIndex.value = (currentIndex.value + 1) % users.value.length;
};

const startAutoSlide = () => {
  interval = setInterval(nextSlide, 5000); // Change the interval as needed
};

const stopAutoSlide = () => {
  clearInterval(interval);
};

const pauseAutoSlide = () => {
  stopAutoSlide();
};

const resumeAutoSlide = () => {
  startAutoSlide();
};

onMounted(() => {
  startAutoSlide();
});

onUnmounted(() => {
  stopAutoSlide();
});
</script>

<style scoped>
.testimonial-slider {
  position: relative;
  overflow: hidden;
  width: 100%;
  margin-top: 96px;
}

.testimonial-container {
  width: 57%;
  overflow: hidden;
  display: flex;
  justify-content: center;
  align-items: center;
  margin: auto;
}

.testimonial .user-testimony {
  width: 57%;
  text-align: center;
  color: var(--grey-900-base);
  text-align: center;
  font-family: var(--primary---font--family);
  font-size: 34px;
  font-style: normal;
  font-weight: 500;
  line-height: 51px;
  letter-spacing: -1px;
}

.testimonials {
  display: flex;
  transition: transform 0.5s ease-in-out;
  margin-bottom: 84px;
}

.testimonial {
  display: flex;
  flex: 0 0 100%;
  flex-direction: column;
  align-items: center;
  justify-content: center;
  gap: 48px;
  box-sizing: border-box;
  padding: 20px;
  text-align: center;
  /* width: 300px; */
  /* border: 1px solid blue; */
  /* margin: 50px; */

}



.pagination-dots {
  position: absolute;
  bottom: 10px;
  left: 50%;
  transform: translateX(-50%);
  display: flex;
  gap: 12px;
}

.user-image {
  width: 32px;
  height: 32px;
  opacity: 0.4;
  cursor: pointer;

}

.user-image.active {
  opacity: 1;
  width: 44px;
  height: 44px;
}
@media screen and (max-width: 1700px) {
  .testimonial-container{
    width: 70%;
  }
  .testimonial .user-testimony{
    width: 70%;
  }
}
@media screen and (max-width: 1500px) {
  .testimonial-container{
    width: 75%;
  }
  .testimonial .user-testimony{
    width: 75%;
  }
}
@media screen and (max-width: 1100px) {
  .testimonial-container{
    width: 80%;
  }
  .testimonial .user-testimony{
    width: 80%;
  }
}
@media screen and (max-width: 675px) {
  .testimonial-container{
    width: 87%;
  }
  .testimonial .user-testimony{
    width: 87%;
text-align: center;
font-size: 20px;
font-style: normal;
font-weight: 500;
line-height: 30px;
letter-spacing: -0.3px;
  }
  .testimonial img {
  /* background: red; */
  width: 200px;
  height: 100px;
  /* border: 1px solid red; */

}
.testimonial {
  display: flex;
  flex: 0 0 100%;
  flex-direction: column;
  align-items: center;
  justify-content: center;
  gap: 24px;


}
.details p{
font-size: 16px;
font-style: normal;
font-weight: 500;
line-height: 24px;
letter-spacing: -0.2px;
}
.details span{
font-size: 12px;
font-style: normal;
font-weight: 400;
line-height: 18px; 
}
}
</style>
    