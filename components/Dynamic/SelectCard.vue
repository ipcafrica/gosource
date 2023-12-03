<template>
  <div
    class="card"
    @click="selectItem(card.value)"
    :class="{ clicked: selectedItem === card.value }"
  >
    <div class="card-top">
      <img :src="card.svg" alt="Card Image" class="card-image" />
      <!-- <svg
        :class="{ selected: isSelected }"
        viewBox="0 0 25 25"
        width="20"
        height="20"
      >
        <circle cx="12" cy="12" r="11" />
      </svg> -->
      <svg
        class="circle"
        :class="{ selected: isSelected }"
        xmlns="http://www.w3.org/2000/svg"
        width="20"
        height="20"
        viewBox="0 0 20 20"
        fill="none"
      >
        <rect
          x="2.50033"
          y="2.50002"
          width="15"
          height="15"
          rx="7.5"
          fill="white"
          stroke="#E4E7EC"
          stroke-width="1.66667"
        />
      </svg>
      <svg
      class="try"
        v-if="isSelected"
        xmlns="http://www.w3.org/2000/svg"
        width="20"
        height="20"
        viewBox="0 0 20 20"
        fill="none"
      >
        <path
          d="M10.0003 1.66666C5.40866 1.66666 1.66699 5.40832 1.66699 9.99999C1.66699 14.5917 5.40866 18.3333 10.0003 18.3333C14.592 18.3333 18.3337 14.5917 18.3337 9.99999C18.3337 5.40832 14.592 1.66666 10.0003 1.66666ZM13.9837 8.08332L9.25866 12.8083C9.14199 12.925 8.98366 12.9917 8.81699 12.9917C8.65033 12.9917 8.49199 12.925 8.37533 12.8083L6.01699 10.45C5.77533 10.2083 5.77533 9.80832 6.01699 9.56666C6.25866 9.32499 6.65866 9.32499 6.90033 9.56666L8.81699 11.4833L13.1003 7.19999C13.342 6.95832 13.742 6.95832 13.9837 7.19999C14.2253 7.44166 14.2253 7.83332 13.9837 8.08332Z"
          fill="#09420C"
        />
      </svg>
    </div>

    <div class="card-content">
      <h4 class="card-title heading-4-bold">
        {{ card.title }}
      </h4>
      <p class="card-snippet body-small-regular">
        {{ card.snippet }}
      </p>
    </div>
  </div>
</template>

<script>
export default {
  props: {
    card: {
      type: Object,
      required: true,
    },
    selectedItem: {
      type: String,
      required: true,
    },
  },
  computed: {
    isSelected() {
      return this.selectedItem === this.card.value;
    },
  },
  methods: {
    selectItem(value) {
      this.$emit("selectItem", value);
      console.log(value);
    },
  },
};
</script>

<style scoped>
.card {
  width: 240px;
  border: 1px solid var(--grey-100);
  border-radius: 16px;
  display: flex;
  flex-direction: column;
  justify-content: center;
  align-items: flex-start;
  gap: 24px;
  cursor: default;
  padding: 20px;
}
.card-top {
  display: flex;
  justify-content: space-between;
  align-items: flex-start;
  width: 100%;
}
.card-content {
  display: flex;
  flex-direction: column;
  gap: 8px;
}
.card-title {
  color: var(--grey-700);
}
.card-snippet {
  color: var(--grey-500);
}

.selected.circle {
  stroke: none;
  fill: var(--supporting-500-base);
  display: none;
}

svg circle {
  stroke: var(--grey-200);
  stroke-width: 1px;
  fill: none;
  width: 20px;
  height: 20px;
}
.try{
  animation: selectedAnimation 0.5s ease-in-out;
}
.card:hover {
  border: 1px solid var(--grey-300);
}

.clicked {
  border: 1px solid var(--orange-300);
  background: var(--orange-25);
}
.clicked:hover, .clicked:active {
  border: 1px solid var(--orange-300);
  background: var(--orange-25);
}

@keyframes clickedAnimation {
  0% {
    border-color: var(--orange-300);
    background-color: var(--orange-25);
    opacity: 0;
  }
  100% {
    border-color: var(--grey-100);
    background-color: transparent;
    opacity: 1;
  }
}

/* Keyframes for selected animation */
@keyframes selectedAnimation {
  0% {
    transform: scale(1);
  }
  50% {
    transform: scale(1.2);
  }
  100% {
    transform: scale(1);
  }
}

@media screen and (max-width: 600px) {
  .card {
    cursor: default;
    padding: 20px;
    width: 100%;
    border: 1px solid var(--grey-100);
    border-radius: 16px;
    display: flex;
    flex-direction: column;
    justify-content: center;
    align-items: flex-start;
    gap: 24px;
    transition: 0.3s ease-in-out;
  }

  .heading-4-bold {
    font-family: var(--graphikSemibold);
    font-size: 18px;
    font-style: normal;
    font-weight: 600;
    line-height: 27px;
    letter-spacing: -0.2px;
  }
  .clicked {
    border: 1px solid var(--orange-300);
    background: var(--orange-25);
  }
}
</style>
<!-- 
<style scoped>
@keyframes clickedAnimation {
  0% {
    border-color: var(--orange-300);
    background-color: var(--orange-25);
    opacity: 0;
  }
  100% {
    border-color: var(--grey-100);
    background-color: transparent;
    opacity: 1;
  }
}

@keyframes selectedAnimation {
  0% {
    transform: scale(1);
  }
  50% {
    transform: scale(1.2);
  }
  100% {
    transform: scale(1);
  }
}

.clicked {
  animation: clickedAnimation 0.3s ease-in-out;
  border: 1px solid var(--orange-300);
  background: var(--orange-25);
}

.selected circle {
  animation: selectedAnimation 0.5s ease-in-out;
  transform-origin: center;
  stroke: none;
  fill: var(--supporting-500-base);
}

</style> -->