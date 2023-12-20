<template>
  <section class="section-wrapper" :class="align">
    <div
      v-if="data"
      class="header-content"
      :class="[flexPosition, left]"
      :style="{ 'max-width': dynamicmaxWidth }"
    >
      <header class="base-font">{{ data.title }}</header>
      <div class="content" :class="[flexPosition, left]">
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

const { maxWidth, data, flexPosition, fontSize, bigFont, left } = defineProps({
  data: {
    required: true,
  },
  flexPosition: {
    type: String,
    default: "left",
  },
  left: {
    type: String,
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
  max-width: 1140px;
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
@media (max-width: 900px) {
  h1 {
    text-align: center;
    font-size: 34px;
    line-height: 44px; /* 129.412% */
    letter-spacing: -1px;
  }

  p {
    text-align: center;
    font-size: 14px;
    line-height: 21px; /* 150% */
    letter-spacing: -0.2px;
  }
  .left h1,
  .left p {
    text-align: left;
    align-items: flex-start;
  }
  .center h1,
  .center p {
    text-align: center;
    align-items: center;
  }
  .right h1,
  .right p {
    text-align: right;
    align-items: flex-end;
  }
}
@media (max-width: 700px) {
  .section-wrapper {
    padding: 72px 0;
  }
}
@media (max-width: 450px) {
  .section-wrapper {
    width: 90%;
  }
  .content.left h1,
  .content.left p {
    text-align: left;
  }
  .header-content.left {
    align-items: flex-start;
  }
}
</style>
