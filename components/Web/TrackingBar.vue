<template>
  <div class="tracking-bar">
    <div class="step">
      <div class="number" :class="{ active: step === 1, finished: step > 1 }">
        <p class="body-micro-bold" v-if="step === 1">1</p>
        <svg
          v-else
          width="24"
          height="24"
          viewBox="0 0 24 24"
          fill="none"
          xmlns="http://www.w3.org/2000/svg"
        >
          <rect width="24" height="24" rx="12" fill="#099137" />
          <path
            d="M16 9L10.5 14.5L8 12"
            stroke="#F9FAFB"
            stroke-width="1.66667"
            stroke-linecap="round"
            stroke-linejoin="round"
          />
        </svg>
      </div>
    </div>
    <div class="line" :class="{ completed: step === 2 || step === 3 }"></div>
    <div class="step">
      <div
        class="number"
        :class="{ active: step === 2 || step === 3, finished: !inValid }"
      >
        <p class="body-micro-bold" v-if="inValid">2</p>
        <svg
          v-else
          width="24"
          height="24"
          viewBox="0 0 24 24"
          fill="none"
          xmlns="http://www.w3.org/2000/svg"
        >
          <rect width="24" height="24" rx="12" fill="#099137" />
          <path
            d="M16 9L10.5 14.5L8 12"
            stroke="#F9FAFB"
            stroke-width="1.66667"
            stroke-linecap="round"
            stroke-linejoin="round"
          />
        </svg>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  props: {
    step: {
      type: Number,
      required: true,
    },
    inValid: {
      type: Boolean,
      required: true,
    },
  },
};
</script>

<style scoped>
.tracking-bar {
  display: flex;
  align-items: center;
  gap: 8px;
}
.step {
  display: flex;
  align-items: center;
  gap: 8px;
}
.number {
  width: 24px;
  height: 24px;
  background-color: #ffffff;
  color: var(--grey-2);
  border: 1px solid var(--grey-2);
  border-radius: 50%;
  display: flex;
  align-items: center;
  justify-content: center;
  transition: all 0.5s;
}
.active {
  color: var(--success-500);
  border: 1px solid var(--success-500);
  animation: scaleUp 0.3s ease-in-out forwards;
}
.line {
  width: 90px;
  height: 2px;
  background: linear-gradient(90deg, var(--success-500) 50%, var(--success-50) 50%);
  transition: background-color 0.5s;
}
.completed {
  background: #28a745;
  animation: fadeInBackground 0.5s ease-in-out forwards;
}
.finished {
  background: #28a745;
  animation: pulse 0.5s infinite alternate;
}

@keyframes scaleUp {
  to {
    width: 24px;
    height: 24px;
    background-color: #ffffff;
    color: var(--success-500);
    border: 1px solid var(--success-500);
    border-radius: 50%;
    display: flex;
    align-items: center;
    justify-content: center;
  }
}

@keyframes pulse {
  to {
    transform: scale(1.1);
  }
}

@keyframes fadeInBackground {
  to {
    background: #28a745;
    color: #ffffff;
    border-color: #28a745;
  }
}
</style>
