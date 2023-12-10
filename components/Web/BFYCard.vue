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
    <DynamicMainButton
      :buttonText="data.buttonText"
      size="s"
      type="link-neutral"
      icon="icon-right"
      class="w-auto"
    >
      <template v-slot:svg>
        <div v-html="isHovered ? arrowRight : caretRight"></div>
      </template>
    </DynamicMainButton>
  </div>
</template>

<script setup>
import { ref } from "vue";
import { caretRight, arrowRight } from "../utils/svg";

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
</style>
