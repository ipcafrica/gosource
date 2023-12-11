<template>
  <div>
    <div class="bfy-wrap">
      <WebBFYCard :data="data" v-for="(data, index) in builtForYou" :key="index">
        <template v-slot:svg>
          <div v-html="data.svg"></div>
        </template>
      </WebBFYCard>
    </div>
    <div class="accordion">
      <WebAccordionWorks/>
    </div>
    <WebSection :data="dummyData[0]" />
    <WebFeatureCard />
    <WebFooter />

  </div>
</template>

<script setup>
import { ref } from "vue";
import { food, car, credit, chat } from "../utils/svg";

const builtForYou = ref([
  {
    svg: food,
    heading: "Order food items in bulk",
    snippet:
      "We offer the best rates on food items and materials as we procure directly from farmers and manufacturers to get you the best at unbeatable prices.",
    buttonText: "Place an order",
  },
  {
    svg: credit,
    heading: "Access to buy on credit",
    snippet:
      "Up to ₦500,000 or more, depending on your supply scale. We allow you fulfil your orders and make payments within 7days.",
    buttonText: "Get access",
  },
  {
    svg: car,
    heading: "24hours delivery",
    snippet:
      "We deliver available products immediately or procure within 24 hours  to allow you operate and serve your customers without delay.",
    buttonText: "Order now",
  },
  {
    svg: chat,
    heading: "Active customer support",
    snippet:
      "People you can trust to assist with your inquiries and provide solutions to your complaints. Your feedback is important to us.",
    buttonText: "Start now",
  },
]);
const dummyData = ref([
  {
    title: "Dummy Title",
    header: "Dummy Header",
    snippet:
      "Lorem ipsum dolor sit amet, consectetur adipiscing elit. Quisque euismod libero ut quam fringilla, et cursus nisl tincidunt.",
    buttonText: "Click Me",
  },
]);
</script>

<style scoped>
.accordion{
  border: 1px solid red;
}
.bfy-wrap {
  display: flex;
  align-items: flex-start;
  gap: 40px;
  align-self: stretch;
  max-width: 80%;
  margin-inline: auto;
}
</style>
