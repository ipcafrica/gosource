<template>
  <button
    @click="$emit('clickButton')"
    class="button"
    :class="buttonClasses"
    :disabled="disabled || isLoading"
  >
    <span v-if="showText && !isLoading">{{ buttonText }}</span>
    <slot v-if="!isLoading" name="svg"></slot>
    <DynamicLoader :size="size" :isLoading="isLoading"/>
  </button>
</template>

<script setup>
import { ref, computed } from "vue";

const { buttonText, size, type, icon, showText, disabled, isLoading } =
  defineProps({
    buttonText: {
      type: String,
    },
    size: {
      type: String,
      required: true,
    },
    type: {
      type: String,
      required: true,
    },
    icon: {
      type: String,
    },
    showText: {
      type: Boolean,
      default: true,
    },
    disabled: {
      type: Boolean,
      default: false,
    },
    isLoading: {
      type: Boolean,
      default: false,
    },
  });

const buttonClasses = computed(() => {
  return {
    "text-button-micro micro": size === "micro",
    "text-button-small small": size === "small",
    "text-button-medium medium": size === "medium",
    "text-button-large large": size === "large",

    // Button type
    "primary-button": type === "primary",
    "secondary-button": type === "secondary",
    "neutral-outline": type === "outline",
    "neutral-filled": type === "filled",
    destructive: type === "destructive",
    "link-primary": type === "link-primary",
    "link-neutral": type === "link-neutral",

    // icon position
    "icon-left": icon === "left",
    "icon-right": icon === "right",
    "icon-button": !showText,
  };
});

</script>

<style scoped>
button {
  gap: 4px;
}

button.large {
  gap: 8px;
}
</style>