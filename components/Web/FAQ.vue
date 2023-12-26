<template>
  <div class="accordion">
    <div
      v-for="(content, index) in accordionContent"
      :key="index"
      class="accordion-content"
      :class="{ open: content.isOpen }"
    >
      <header @click="toggleAccordion(index)">
        <span class="title display-font text-heading-4-meduim medium text-grey-700">
          {{ content.title }}
        </span>
        <div class="icon">
          <span></span>
          <span></span>
        </div>
      </header>

      <p
        class="description text-body-large-regular regular text-grey-700"
        :style="{ height: content.isOpen ? content.height + 'px' : '0px' }"
      >
        {{ content.description }}
      </p>
    </div>
  </div>
</template>

<script setup>
import { ref } from "vue";

const accordionContent = ref([
  {
    title: "How does GoSource work?",
    description:
      "In the dynamic landscape of modern business, the demand for streamlined and efficient processes has never been more critical. One area that often faces complexities is food procurement, supply-chain management, and logistics.",
    isOpen: false,
    height: 0,
  },
  {
    title: "How much credit am I eligible for?",
    description:
      "In the dynamic landscape of modern business, the demand for streamlined and efficient processes has never been more critical. One area that often faces complexities is food procurement, supply-chain management, and logistics.",
    isOpen: false,
    height: 0,
  },
  {
    title: "How long before you deliver?",
    description:
      "In the dynamic landscape of modern business, the demand for streamlined and efficient processes has never been more critical. One area that often faces complexities is food procurement, supply-chain management, and logistics.",
    isOpen: false,
    height: 0,
  },
  {
    title: "How do I sign up?",
    description:
      "In the dynamic landscape of modern business, the demand for streamlined and efficient processes has never been more critical. One area that often faces complexities is food procurement, supply-chain management, and logistics.",
    isOpen: false,
    height: 0,
  },
  {
    title: "How do I access credit?",
    description:
      "In the dynamic landscape of modern business, the demand for streamlined and efficient processes has never been more critical. One area that often faces complexities is food procurement, supply-chain management, and logistics.",
    isOpen: false,
    height: 0,
  },
]);

const toggleAccordion = (index) => {
  accordionContent.value.forEach((item, i) => {
    if (index !== i) {
      item.isOpen = false;
    }
  });

  const content = accordionContent.value[index];
  content.isOpen = !content.isOpen;
  if (content.isOpen) {
    content.height = getContentHeight(index);
  }
};

const getContentHeight = (index) => {
  const descriptionElement = document.querySelectorAll(".description")[index];
  return descriptionElement.scrollHeight;
};
</script>

<style scoped>
.icon {
  position: relative;
  display: flex;
  align-items: center;
}

.icon span {
  display: block;
  width: 16px;
  height: 2px;
  border-radius: 5px;
  background: var(--grey-500);
  transition: all var(--animation-duration) ease-in-out;
}
.icon span:nth-child(2) {
  position: absolute;
  rotate: 90deg;
  opacity: 1;
}
.open .icon span:nth-child(2) {
  rotate: 0deg;
  opacity: 0;
}

.accordion {
  margin-top: 72px;
  display: flex;
  max-width: 783px;
  flex-direction: column;
  align-items: flex-start;
  gap: 8px;
  width: 100%;
}

p {
  text-align: left;
}

.accordion .accordion-content {
  margin: 10px 0;
  border-radius: 4px;
  overflow: hidden;
}

.accordion-content.open {
  padding-bottom: 10px;
}

.accordion-content header {
  cursor: pointer;
  text-align: left;
  display: flex;
  padding: 24px;
  justify-content: space-between;
  align-items: center;
  align-self: stretch;
  transition: all 0.2s linear;
}

.accordion-content.open header {
  padding-bottom: 16px;
}

.accordion-content .description {
  height: 0;
  padding: 0 24px;
  transition: all 0.2s linear;
}

@media (max-width: 900px) {
  .accordion-content header {
    padding: 16px 12px;
  }
  header span.title {
    font-size: 16px;
    font-style: normal;
    line-height: 24px; /* 150% */
    letter-spacing: -0.2px;
  }
  header span.description {
    font-size: 14px;
    line-height: 21px; /* 150% */
    letter-spacing: -0.2px;
  }

  .accordion-content .description {
    padding: 0 12px;
  }
}
</style>
