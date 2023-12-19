<template>
  <div>
    <div class="display-container">
      <div
        v-for="(person, index) in people"
        :key="index"
        ref="peopleDivs"
        class="person"
        :class="{ 'displayed': currentIndex === index }"
      >
        <h2>{{ person.name }}</h2>
        <p>{{ person.jobTitle }}</p>
        <p>{{ person.snippet }}</p>
      </div>
      <div class="image-container">
        <div
          v-for="(person, index) in people"
          :key="index"
          class="image"
          @click="selectPerson(index)"
          @mouseover="pauseAnimation"
          @mouseleave="resumeAnimation"
          :style="{ width: currentIndex === index ? '20px' : '16px', height: currentIndex === index ? '20px' : '16px' }"
        >
          <img :src="person.svg" alt="Person Image" />
        </div>
      </div>
    </div>
  </div>
</template>

<script setup>
import { ref, onMounted, onUnmounted } from 'vue';

const people = ref([
  {
    name: 'John Doe',
    jobTitle: 'Software Engineer',
    snippet: 'Passionate about creating innovative software solutions.',
    svg: '/business.svg',
  },
  {
    name: 'Jane Smith',
    jobTitle: 'Graphic Designer',
    snippet: 'Bringing creativity to life through visual design.',
    svg: '/business.svg',
  },
  {
    name: 'Alex Johnson',
    jobTitle: 'Marketing Specialist',
    snippet: 'Crafting compelling marketing strategies for success.',
    svg: '/business.svg',
  },
]);

const currentIndex = ref(0);
let animationInterval;
const containerWidth = 500;

const peopleDivs = ref([]);

const selectPerson = (index) => {
  const current = currentIndex.value;
  currentIndex.value = index;

  if (index !== current) {
    animateTransition(current, index);
  }

  startAutoSlide();
};

const animateTransition = (fromIndex, toIndex) => {
  const direction = fromIndex < toIndex ? -1 : 1;
  const personWidth = containerWidth;

  const fromTransform = `translateX(${direction * personWidth}px)`;
  const toTransform = 'translateX(0)';

  // Slide out the current person
  peopleDivs.value[fromIndex].style.transform = fromTransform;
  peopleDivs.value[fromIndex].style.animation = 'slide-out 2s forwards';

  // Reset the transform for the next animation
  setTimeout(() => {
    peopleDivs.value[fromIndex].style.transform = '';
    peopleDivs.value[fromIndex].style.animation = '';
  }, 500);

  // Slide in the new person
  peopleDivs.value[toIndex].style.transform = toTransform;
};

const startAutoSlide = () => {
  clearInterval(animationInterval);
  animationInterval = setInterval(() => {
    const nextIndex = (currentIndex.value + 1) % people.value.length;
    selectPerson(nextIndex);
  }, 5000);
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
.display-container {
  position: relative;
  width: 500px;
  border: 1px solid red;
  overflow: hidden;
}

.person {
  display: none;
  animation: slide-in 2s forwards;
}

.person.displayed {
  display: block;
}

.image-container {
  position: absolute;
  bottom: 0;
  display: flex;
  justify-content: space-around;
  width: 100%;
}

.image {
  background-color: #3498db;
  cursor: pointer;
  display: flex;
  align-items: center;
  justify-content: center;
  overflow: hidden;
  transition: all 0.5s ease;
}

.image img {
  width: 100%;
  height: 100%;
  object-fit: cover;
}

@keyframes slide-in {
  from {
    transform: translateX(100%);
  }
  to {
    transform: translateX(0);
  }
}

@keyframes slide-out {
  from {
    transform: translateX(0);
  }
  to {
    transform: translateX(-100%);
  }
}
</style>
