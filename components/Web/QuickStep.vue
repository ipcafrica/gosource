<template>
  <div class="quick-step-wrap">
    <div class="wrapper">
      <div class="container" v-for="(data, index) in data" :key="index">
        <div class="progress-bar">
          <div class="ring base-font current bg-grey-200">{{ index + 1 }}</div>
          <div class="bar bg-grey-200" v-if="index !== 2"><span></span></div>
        </div>
        <div class="content-wrap">
          <div class="content">
            <h5 class="title text-heading-5-medium medium text-grey-900-base">
              {{ data.title }}
            </h5>
            <p class="snippet text-body-large-regular regular text-grey-700">
              {{ data.snippet }}
            </p>
          </div>
        </div>
      </div>
    </div>
    <div class="img-container">
      <div class="" v-html="quickStep"></div>
    </div>
  </div>
</template>

<script setup>
import { quickStep } from "../utils/svg";
import { ref, onMounted } from "vue";

const {} = defineProps({
  data: {
    type: Object,
    required: true,
  },
});

const step = ref(1);

onMounted(() => {
  const intervalId = setInterval(() => {
    // Update the value of 'step' every 3 seconds
    step.value = (step.value % 3) + 1;
  }, 3000);

  // Clean up the interval when the component is unmounted
  onBeforeUnmount(() => {
    clearInterval(intervalId);
  });
});
</script>

<style scoped>
h5,
p {
  text-align: left;
}
.quick-step-wrap {
  display: flex;
  justify-content: space-between;
  align-items: flex-start;
  align-self: stretch;
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
  line-height: 19.2px; /* 150% */
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
  height: 100%;
  background: var(--primary-primary-500-base);
  transition: all 4s linear;
}

.ring.current {
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
</style>
