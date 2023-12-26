<template>
  <div class="quick-step-wrap">
    <div class="paginate">
      <span
        v-for="(data, index) in data"
        :key="index"
        :class="{ current: step === index + 1 }"
      ></span>
    </div>
    <div class="wrapper">
      <div class="container" v-for="(data, index) in data" :key="index">
        <div class="progress-bar" :class="{ current: step === index + 1 }">
          <div class="ring base-font bg-grey-200">{{ index + 1 }}</div>
          <div class="bar bg-grey-200" v-if="index !== 2"><span></span></div>
        </div>
        <div class="content-wrap">
          <div class="content" :class="{ current: step === index + 1 }">
            <h5 class="title text-heading-5-medium medium text-grey-200">
              {{ data.title }}
            </h5>
            <p class="snippet text-body-large-regular regular text-grey-200">
              {{ data.snippet }}
            </p>
          </div>
        </div>
      </div>
    </div>

    <div class="webp-wrap">
      <div class="img-wrap">
        <img :src="getWebPImage(step)" alt="WebP Image" />
      </div>
    </div>
  </div>
</template>

<script setup>
import { ref, onMounted, onBeforeUnmount } from "vue";

const { data } = defineProps({
  data: {
    type: Object,
    required: true,
  },
});

const step = ref(1);
let intervalId;

onMounted(() => {
  intervalId = setInterval(() => {
    step.value = (step.value % 3) + 1;
  }, 9000);
});

onBeforeUnmount(() => {
  clearInterval(intervalId);
});

const getWebPImage = (step) => {
  return `/images/${step}.webp`;
};
</script>

<style scoped>
h5,
p {
  text-align: left;
  transition: all var(--animation-duration) linear;
}

.mobile-setup {
  display: none;
}

.quick-step-wrap {
  display: flex;
  justify-content: space-between;
  align-items: center;
  align-self: stretch;
}

.paginate {
  display: none;
}

.container {
  display: flex;
  align-items: flex-start;
  gap: 24px;
  min-height: 147px;
}

.progress-bar {
  display: flex;
  /* height: 329px; */
  flex-direction: column;
  align-items: center;
  gap: 8px;
}

.ring {
  color: var(--White);
  font-size: 12.8px;
  font-weight: 600;
  line-height: 19.2px;
  /* 150% */
  letter-spacing: -0.16px;

  display: flex;
  width: 32px;
  height: 32px;
  padding: 8px;
  flex-direction: column;
  justify-content: center;
  align-items: center;
  gap: 8px;
  flex-shrink: 0;

  border-radius: 80px;
  transition: all var(--animation-duration) ease-in-out;
}

.bar {
  position: relative;
  height: 100px;
  width: 3px;
}

.bar span {
  position: absolute;
  top: 0;
  left: 0;
  width: 100%;
  height: 0;
  opacity: 1;
  transition: height 9s linear;
}

.current .bar span,
.final .bar span,
.complete .bar span {
  height: 100%;
  background: var(--primary-primary-500-base);
}

.current .ring,
.final .ring,
.complete .ring {
  background: var(--primary-primary-500-base);
}

.content {
  display: flex;
  flex-direction: column;
  align-items: flex-start;
  gap: 8px;
}

.content p {
  max-width: 309.297px;
}
.current h5 {
  color: var(--grey-900-base);
}
.current p {
  color: var(--grey-700);
}

.webp-wrap {
  display: flex;
  max-width: 604px;
  padding: 51px 55px 0px 54px;
  justify-content: center;
  align-items: center;
  border-radius: 16px;
  background: var(--grey-50);
}

.img-wrap {
  width: 492px;
  height: 544px;
  overflow: hidden;
}

.img-wrap img {
  width: 100%;
  height: 100%;
  object-fit: cover;
}

@media (max-width: 1200px) {
  .mobile-setup {
    display: none;
    flex-direction: column;
    align-items: center;
    gap: 8px;
    align-self: stretch;
  }
  .quick-step-wrap {
    flex-direction: column-reverse;
    align-items: center;
    gap: 32px;
  }
  .svg {
    width: auto;
  }
  .wrapper {
    display: flex;
  }

  .progress-bar {
    display: none;
    overflow: hidden;
    height: 0;
    width: 0;
  }
  .content {
    opacity: 0;
    width: 0;
    height: 0;
    overflow: hidden;
    align-items: center;
  }
  .content.current {
    opacity: 1;
    width: 100%;
    height: auto;
  }

  .container {
    min-height: auto;
  }

  h5,
  p {
    text-align: center;
  }

  .paginate {
    display: flex;
    justify-content: center;
    align-items: flex-start;
    gap: 12px;
  }

  .paginate span.current {
    background: var(--grey-500);
  }

  .paginate span {
    width: 16px;
    height: 16px;
    border-radius: 1000px;
    background: var(--grey-200);
  }
  .webp-wrap {
    max-width: 100%;
    padding: 27.651px 29.82px 0px 29.277px;
  }

  .img-wrap {
    width: 100%;
    height: 100%;
  }
}

@media (max-width: 960px) {
  
}

</style>
