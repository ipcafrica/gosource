<template>
  <div
    class="bfycard-wrapper"
    @mouseenter="handleMouseEnter"
    @mouseleave="handleMouseLeave"
  >
    <slot name="svg" />
    <div class="content">
      <h5 class="text-heading-5-medium medium text-grey-900-base">{{ data.heading }}</h5>
      <p class="text-body-small-regular regular text-grey-700">{{ data.snippet }}</p>
    </div>
    <div class="cta">
      <span class="base-font text-button-small medium text-grey-700">{{
        data.buttonText
      }}</span>
      <div class="hamburger is-active" id="hamburger-4">
        <span class="line"></span>
        <span class="line"></span>
        <span class="line"></span>
      </div>
    </div>
  </div>
</template>

<script setup>
import { ref } from "vue";

const isHovered = ref(false);

defineProps({
  data: {
    type: Object,
    required: true,
  },
});

function handleMouseEnter() {
  isHovered.value = true;
}

function handleMouseLeave() {
  isHovered.value = false;
}
</script>

<style scoped>
.bfycard-wrapper {
  max-width: 255px;
  cursor: pointer;
  display: flex;
  flex-direction: column;
  align-items: flex-start;
  gap: 16px;
}
.content {
  display: flex;
  flex-direction: column;
  align-items: flex-start;
  gap: 8px;
  align-self: stretch;
}
.cta {
  display: flex;
  justify-content: center;
  align-items: center;
  gap: 4px;
}
span.line {
  background: var(--grey-700);
}

.hamburger {
  width: max-content;
}

.hamburger .line {
  width: 7px;
  height: 2px;
  border-radius: 5px;
  background-color: var(--grey-700);
  display: block;
  -webkit-transition: all 0.3s ease-in-out;
  -o-transition: all 0.3s ease-in-out;
  transition: all 0.3s ease-in-out;
}
#hamburger-4 .line:nth-child(2) {
  opacity: 0;
  margin-left: 0%;
}

.bfycard-wrapper:hover #hamburger-4 .line:nth-child(1),
.bfycard-wrapper:hover #hamburger-4 .line:nth-child(3) {
  width: 7px;
}

.bfycard-wrapper:hover #hamburger-4 .line:nth-child(2) {
  opacity: 1;
  margin-left: 100%;
}

#hamburger-4 .line:nth-child(1) {
  -webkit-transform: translateX(10px) rotate(45deg);
  -ms-transform: translateX(10px) rotate(45deg);
  -o-transform: translateX(10px) rotate(45deg);
  transform: translateX(10px) rotate(45deg);
}

#hamburger-4 .line:nth-child(3) {
  -webkit-transform: translateX(10px) rotate(-45deg);
  -ms-transform: translateX(10px) rotate(-45deg);
  -o-transform: translateX(10px) rotate(-45deg);
  transform: translateX(10px) rotate(-45deg);
}
.bfycard-wrapper:hover .cta span {
  color: var(--grey-900);
}
.bfycard-wrapper:hover .hamburger .line {
  background-color: var(--primary-primary-500-base);
}

h5,
p {
  text-align: left;
}
@media (max-width: 450px) {
  .bfycard-wrapper {
    max-width: 100%;
  }
}
</style>
