<template>
  <div>
    <div class="bg-grey-100">
      <WebSection
        :data="sectionData[0]"
        flexPosition="left"
        align="start"
        maxWidth="499px"
      >
        <template v-slot:content>
          <WebFeatureCard />
        </template>
      </WebSection>
    </div>
    <WebSection :data="sectionData[1]" flexPosition="center" maxWidth="458px">
      <template v-slot:content>
        <div class="bfy-wrap mt-128">
          <WebBFYCard :data="data" v-for="(data, index) in builtForYou" :key="index">
            <template v-slot:svg>
              <div v-html="data.svg"></div>
            </template>
          </WebBFYCard>
        </div>
      </template>
    </WebSection>
    <div class="bg-grey-200">
      <WebSection :data="sectionData[2]" flexPosition="center">
        <template v-slot:content> </template>
      </WebSection>
    </div>
    <div class="bg-supporting-900">
      <WebSection
        :data="sectionData[3]"
        flexPosition="center"
        maxWidth="1009px"
        bigFont="text-white text-display-regular bold"
      >
        <template v-slot:content> </template>
      </WebSection>
    </div>

    <!-- testimonials here -->

    <WebSection :data="sectionData[4]" flexPosition="center">
      <template v-slot:content>
        <!-- Faq section here -->
      </template>
    </WebSection>
    <div class="bg-grey-50">
      <WebSection :data="sectionData[5]" flexPosition="center" maxWidth="458px" />
    </div>
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
const sectionData = ref([
  {
    id: 0,
    title: "Hassle-Free",
    header: "Let’s manage your procurement process",
    snippet:
      "We are a food procurement, supply-chain, and logistics powerhouse that take responsibilities off businesses and consumers and keeps the supply chain running.",
    buttonText: "Start now",
  },
  {
    id: 1,
    title: "Built for you",
    header: "Run your business with zero stress",
    snippet: null,
    buttonText: null,
  },
  {
    id: 2,
    title: "Quick steps",
    header: "Place your first order",
    snippet: null,
    buttonText: null,
  },
  {
    id: 3,
    title: "Zero stress",
    header: "Focus more on cooking, let’s go to the market for you",
    snippet: null,
    buttonText: "Start ordering",
  },
  {
    id: 4,
    title: "FAQ",
    header: "Frequently asked questions",
    snippet: null,
    buttonText: "Start ordering",
  },
  {
    id: 5,
    title: "Let’s go!",
    header: "Get started for free",
    snippet:
      "Start ordering on GoSource today to make the process of buying food items very easy for your business.",
    buttonText: "Start now",
  },
]);
</script>

<style scoped>
.bfy-wrap {
  display: flex;
  align-items: flex-start;
  gap: 40px;
  align-self: stretch;
  margin-inline: auto;
}
.mt-128 {
  margin-top: 128px;
}
</style>
