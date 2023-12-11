<template>
  <section class="section-wrapper" :class="align">
    <div
      v-if="data"
      class="header-content"
      :class="[flexPosition]"
      :style="{ 'max-width': dynamicmaxWidth }"
    >
      <header class="base-font">{{ data.title }}</header>
      <div class="content" :class="[flexPosition]">
        <h1 :class="bigFont">
          {{ data.header }}
        </h1>
        <p class="text-body-large-regular regular text-grey-700">
          {{ data.snippet }}
        </p>
      </div>
      <DynamicButtonMain
        v-if="data.buttonText"
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
import { ref } from "vue";
import { caretRightWhite } from "../utils/svg";

const { maxWidth, data, flexPosition, fontSize, bigFont } = defineProps({
  data: {
    required: true,
  },
  flexPosition: {
    type: String,
    default: "left",
  },
  maxWidth: {
    type: String,
  },
  bigFont: {
    type: String,
    default: "text-grey-900-base text-heading-1-medium medium",
  },
  align: {
    type: String,
    default: "center",
  },
});

const dynamicmaxWidth = ref(maxWidth || "100%");
</script>

<style scoped>
.section-wrapper {
  display: flex;
  max-width: 1440px;
  width: 80%;
  margin-inline: auto;
  padding: 96px 0;
  flex-direction: column;
}

.section-wrapper.center {
  align-items: center;
}
.section-wrapper.start {
  align-items: flex-start;
}
.section-wrapper.end {
  align-items: flex-end;
}
.header-content {
  display: flex;
  flex-direction: column;
  align-items: center;
  gap: 32px;
  width: 100%;
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
  text-align: left;
  align-items: flex-start;
}
.center {
  text-align: center;
  align-items: center;
}
.right {
  text-align: right;
  align-items: flex-end;
}
</style>
