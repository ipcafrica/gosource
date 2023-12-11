<template>
  <section class="section-wrapper">
    <div class="header-content" :class="[flexPosition]">
      <header class="base-font">{{ data.title }}</header>
      <div class="content">
        <h1 class="text-heading-1-medium medium text-grey-900-base">
          {{ data.header }}
        </h1>
        <p class="text-body-large-regular regular text-grey-700">
          {{ data.snippet }}
        </p>
      </div>
      <DynamicButtonMain
        size="medium"
        type="primary"
        icon="icon-right"
        :buttonText="data.buttonText"
        class="w-auto"
      >
        <template v-slot:svg>
          <div v-html="caretRightWhite"></div>
        </template>
      </DynamicButtonMain>
    </div>
    <slot name="content" />
  </section>
</template>

<script setup>
import { caretRightWhite } from "../utils/svg";

defineProps({
  data: {
    type: Object,
    required: true,
  },
  flexPosition: {
    type: String,
    default: "left",
  },
});
</script>

<style scoped>
.section-wrapper {
  display: flex;
  max-width: 1440px;
  width: 80%;
  /* padding: 96px 150px; */
  flex-direction: column;
  align-items: center;
  gap: 128px;
}
.header-content {
  display: flex;
  flex-direction: column;
  align-items: center;
  gap: 32px;
}
header {
  color: var(--orange-orange-500);
  font-family: Inter;
  font-size: 18px;
  font-style: normal;
  font-weight: 500;
  line-height: 24px; /* 133.333% */
  letter-spacing: 0.36px;
}
.content {
  display: flex;
  flex-direction: column;
  gap: 8px;
}
.left {
    align-items: flex-start;
}
</style>
