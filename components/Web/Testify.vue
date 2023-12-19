<template>
  <div class="container">
    <div class="display-container">
      <div
        class="person"
        v-for="(user, index) in users"
        :key="index"
        ref="peopleDivs"
        :class="{ displayed: currentIndex === index }"
      >
        <img :src="user.logo" />
        <p>
          {{ user.testimony }} <span class="new text-grey-500">{{ user.continue }}</span>
        </p>
        <div class="details">
          <p class="text-heading-5-medium medium text-grey-900-base">{{ user.name }}</p>
          <span class="text-body-small-regular regular text-grey-700">{{ user.post }}</span>
        </div>
      </div>

      <div class="image-container">
        <div class="user-image" 
        v-for="(user, index) in users" :key="index"
        :class="{ 'active': currentIndex === index }"
        @click="selectPerson(index)"
          @mouseover="pauseAnimation"
          @mouseleave="resumeAnimation"
          ref="userImages"
        >
          <img :src="user.image" />
        </div>
      </div>
    </div>
  </div>
</template>

<script setup>
import { ref, onMounted, onUnmounted } from "vue";

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

const currentIndex = ref(0)
let animationInterval;
const containerWidth = 825

const peopleDivs =  ref([])

const userImages = ref([]);

const selectPerson = (index) => {
  const current = currentIndex.value;
  currentIndex.value = index;

  if (index !== current) {
    animateTransition(current, index);
  }

  startAutoSlide();
};
const animateTransition = (fromIndex, toIndex) => {
  const direction = fromIndex < toIndex ? 1 : -1;
  const personWidth = containerWidth;

  const fromTransform = `translateX(${direction * personWidth}px)`;
  const toTransform = 'translateX(0)';

  // Slide out the current person if going to the previous index
  if (fromIndex > toIndex) {
    peopleDivs.value[fromIndex].style.transform = fromTransform;
    peopleDivs.value[fromIndex].style.animation = 'slide-out 0.3s forwards';
  } else {
    // Slide in the new person if going to the next index
    peopleDivs.value[toIndex].style.transform = fromTransform;
    peopleDivs.value[toIndex].style.animation = 'slide-in 0.3s forwards';
  }

  // Reset the transform for the next animation
  setTimeout(() => {
    if (fromIndex > toIndex) {
      peopleDivs.value[fromIndex].style.transform = '';
      peopleDivs.value[fromIndex].style.animation = '';
    } else {
      peopleDivs.value[toIndex].style.transform = toTransform;
      peopleDivs.value[toIndex].style.animation = '';
    }
  }, 500);
};


const startAutoSlide = () => {
  clearInterval(animationInterval);
  animationInterval = setInterval(() => {
    const nextIndex = (currentIndex.value + 1) % users.value.length;
    const direction = currentIndex.value < nextIndex ? 1 : -1;

    if (direction === 1) {
      animateTransition(currentIndex.value, nextIndex);
    } else {
      animateTransition(currentIndex.value, nextIndex);
    }

    currentIndex.value = nextIndex;
  }, 2000);
};

const pauseAnimation = () => {
  clearInterval(animationInterval);
};

const resumeAnimation = () => {
  startAutoSlide();
};

onMounted(() => {
  startAutoSlide();
});

onUnmounted(() => {
  clearInterval(animationInterval);
});
</script>

<style scoped>
.container{
    margin-top: 100px;
    /* border: 1px solid red; */
    display: flex;
    justify-content: center;
    align-items: center;
}
.display-container{
    position: relative;
    max-width:100% ;
    display: flex;
    justify-content: center;
    align-items: center;
    gap: 48px;
    flex-direction: column;
    width: 825px;
    overflow: hidden;
    /* border: 1px solid blue; */
}
.person{
    display: none;
    animation: slide-in 1s forwards;
    /* border: 1px solid red; */
    height: max-content;
}

.person p{
    text-align: center;
    color: var(--grey-900-base);
text-align: center;
font-family: var(--primary---font--family);
font-size: 24px;
font-style: normal;
font-weight: 500;
/* line-height: 51px; */
letter-spacing: -1px;
}
.person p .new{
    /* color: var(--grey-500); */
    /* font-size: 10px; */
}
.person.displayed{
    display: flex;
    flex-direction: column;
    align-items: center;
    justify-content: center;
    gap: 48px;
}

.image-container{
    display: flex;
    align-items: center;
    justify-content: center;
    gap: 12px;
    transition: all 1s ease;
    cursor: pointer;
    /* border: 1px solid red; */
}
.user-image{
    width: 32px;
    height: 32px;
    opacity: 0.4;
 
}

.user-image.active{
    opacity: 1;
    width: 44px;
    height: 44px;
}
@keyframes slide-in {
  from {
    transform: translateX(100%);
  }
  to {
    transform: translateX(0);
  }
}

</style>