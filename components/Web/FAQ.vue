<template>
  <div class="accordion">
    <div
      v-for="(content, index) in accordionContent"
      :key="index"
      class="accordion-content"
      :class="{ open: content.isOpen }"
    >
      <header @click="toggleAccordion(index)">
        <span class="title display-font text-heading-4-meduim medium text-grey-700 h1">
          {{ content.title }}
        </span>
        <div class="icon">
          <span></span>
          <span></span>
        </div>
      </header>

      <p
        class="description text-body-large-regular regular text-grey-700s"
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
    title: "Do you offer customized or specialty items upon request?",
    description:
      "Yes, we specialize in providing customized and specialty items tailored to your restaurant's specific needs. Feel free to inquire about any unique requirements.",
    isOpen: false,
    height: 0,
  },
  {
    title: "What are your delivery times and shipping costs?",
    description:
      "Our delivery times vary based on location and order specifics. Shipping costs are calculated based on order size. We aim for timely deliveries and competitive shipping rates.",
    isOpen: false,
    height: 0,
  },
  {
    title:
      "What is your return or exchange policy if we receive damaged or incorrect items?",
    description:
      "In case of damaged or incorrect items, please notify us immediately. We have a hassle-free return and exchange policy. We'll arrange for replacements or refunds as per your preference.",
    isOpen: false,
    height: 0,
  },
  {
    title: "How do you handle backorders or items out of stock?",
    description:
      "If an item is out of stock or on backorder, we'll promptly inform you and provide estimated restocking dates. You can choose to wait or make alternative arrangements.",
    isOpen: false,
    height: 0,
  },
  {
    title: "Is there a dedicated account manager or point of contact for our restaurant?",
    description:
      "Yes, we assign a dedicated account manager to each restaurant to ensure personalized service and smooth communication for all your needs.",
    isOpen: false,
    height: 0,
  },
  {
    title: "What payment methods do you accept?",
    description:
      "We accept various payment methods, including credit/debit cards, bank transfers, and other secure online payment options for your convenience.",
    isOpen: false,
    height: 0,
  },
  {
    title: "Can you assist with sourcing rare or hard-to-find ingredients/products?",
    description:
      "Absolutely, we have extensive networks and expertise to assist in sourcing rare or hard-to-find ingredients/products. Just let us know your requirements.",
    isOpen: false,
    height: 0,
  },
  {
    title: "What types of credit facilities do you offer for restaurants?",
    description: "We offer diverse credit facilities, tailored to restaurant needs.",
    isOpen: false,
    height: 0,
  },
  {
    title: "What are the eligibility criteria for obtaining a credit facility?",
    description:
      "Eligibility criteria typically involve factors like credit history, business revenue, and time in operation. Our team will guide you through the specific requirements.",
    isOpen: false,
    height: 0,
  },
  {
    title: "What is the maximum/minimum credit limit available?",
    description:
      "The credit limits vary based on several factors. We assess your needs and financial situation to determine the most suitable credit limit for your restaurant.",
    isOpen: false,
    height: 0,
  },
  {
    title: "What are the interest rates or fees associated with the credit facility?",
    description:
      "Interest rates and fees depend on the type of credit facility and individual circumstances. Our team will provide transparent information on rates and fees applicable to your chosen facility.",
    isOpen: false,
    height: 0,
  },
  {
    title: "Do you offer flexible repayment options or schedules?",
    description:
      "Yes, we understand the importance of flexibility. We offer various repayment options and schedules tailored to accommodate your restaurant's cash flow and needs.",
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
.h1 {
  max-width: 500px;
}
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
  width: 100%;
  border-radius: 4px;
  overflow: hidden;
}

.accordion-content.open {
  padding-bottom: 24px;
  border-radius: 16px;
  background: var(--grey-75);
}
.accordion-content.open header .title{
  color: var(--grey-900-base);
}

.accordion-content header {
  cursor: pointer;
  text-align: left;
  display: flex;
  padding: 24px;
  justify-content: space-between;
  align-items: center;
  gap: 16px;
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
    max-width: 500px;
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
