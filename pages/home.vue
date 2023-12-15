<template>
  <div>
    <WebNews />
    <div class="bg-orange-25">
      <WebHero data-aos="zoom-in-up" ref="revealType" />
    </div>
    <!-- logo -->
    <WebSection data-aos="zoom-in-up" :data="null">
      <template v-slot:content>
        <div class="client" data-aos="zoom-in-up">
          <h3 class="heading-3-medium medium text-grey-900">
            Trusted by 100+ businesses across the Nation
          </h3>
          <div class="logos">
            <img
              :src="image"
              alt=""
              v-for="(image, index) in images"
              :key="index"
              data-aos="zoom-in-up"
            />
          </div>
        </div>
      </template>
    </WebSection>
    <!-- Hassle-Free -->
    <div class="bg-grey-100">
      <WebSection
        :data="sectionData[0]"
        flexPosition="left"
        align="start"
        maxWidth="499px"
        data-aos="zoom-in-up"
      >
        <template v-slot:content>
          <div class="feature-wrap mt-128">
            <div
              v-for="(data, index) in featureCardData"
              :key="index"
              :class="'feature-item' + (index + 1)"
              data-aos="zoom-in-up"
            >
              <WebFeatureCard :data="data" class="w-auto">
                <template v-slot:svg>
                  <div v-html="data.svg"></div>
                </template>
              </WebFeatureCard>
            </div>
          </div>
        </template>
      </WebSection>
    </div>
    <!-- Built for you -->
    <WebSection
      data-aos="zoom-in-up"
      :data="sectionData[1]"
      flexPosition="center"
      maxWidth="458px"
      left="left"
    >
      <template v-slot:content>
        <div class="bfy-wrap mt-128" data-aos="zoom-in-up">
          <WebBFYCard
            :data="data"
            v-for="(data, index) in builtForYou"
            :key="index"
            data-aos="zoom-in-up"
          >
            <template v-slot:svg>
              <div v-html="data.svg"></div>
            </template>
          </WebBFYCard>
        </div>
      </template>
    </WebSection>
    <!-- Quick steps -->
    <div class="" data-aos="zoom-in-up">
      <WebSection :data="sectionData[2]" flexPosition="center">
        <template v-slot:content>
          <WebQuickStep class="mt-128" :data="quickStep" data-aos="zoom-in-up" />
        </template>
      </WebSection>
    </div>
    <!-- Zero stress -->
    <div class="bg-supporting-900">
      <WebSection
        :data="sectionData[3]"
        flexPosition="center"
        maxWidth="1009px"
        bigFont="text-white text-display-regular bold"
        data-aos="zoom-in-up"
      >
        <template v-slot:content>
          <div class="img mt-128">
            <img src="/assets/images/zero-stress.png" alt="" data-aos="zoom-in-up" />
          </div>
        </template>
      </WebSection>
    </div>

    <!-- testimonials here -->
    <!-- FAQ -->
    <WebSection :data="sectionData[4]" flexPosition="center" data-aos="zoom-in-up">
      <template v-slot:content>
        <WebFAQ data-aos="zoom-in-up" />
      </template>
    </WebSection>
    <!-- Let’s go! -->
    <div class="bg-grey-50" data-aos="zoom-in-up">
      <WebSection
        :data="sectionData[5]"
        flexPosition="center"
        maxWidth="458px"
        data-aos="zoom-in-up"
      />
    </div>
    <WebFooter data-aos="zoom-in-up" />
  </div>
</template>

<script setup>
import { ref, onMounted } from "vue";
import AOS from "aos";
import "aos/dist/aos.css";
import Lenis from "@studio-freight/lenis";
import { food, car, credit, chat, store, invoice, order, insight } from "../utils/svg";

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
    buttonText: null,
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
const images = ref([
  "/images/papasgril.png",
  "/images/wingbistro.svg",
  "/images/spicycorner.png",
  "/images/grillshark.png",
  "/images/redkitchen.png",
  "/images/citysub.png",
]);
const featureCardData = ref([
  {
    img: "/images/store.svg",
    svg: store,
    svgName: "Store",
    title: "All food items in one store",
    snippet:
      "Buy all your quality food items in bulk in one store without going to the market.",
    buttonText: "Place an order",
    color: "bg-wine-50",
  },
  {
    img: "/images/woman.png",
    svg: null,
    svgName: null,
    title: null,
    snippet: null,
    buttonText: null,
    color: "",
  },
  {
    img: "/images/invoice.svg",
    svg: invoice,
    svgName: "Invoice",
    title: "Instant order invoice",
    snippet: "Get instant invoice immediately after you checkout.",
    buttonText: "Get started",
    color: "bg-primary-50",
  },
  {
    img: "/images/orders.svg",
    svg: order,
    svgName: "Orders",
    title: "Track your orders",
    snippet: "You can track the status of your order at every step of the way.",
    buttonText: "Place an order",
    color: "bg-purple-50",
  },
  {
    img: "/images/man.png",
    svg: null,
    svgName: null,
    title: null,
    snippet: null,
    buttonText: null,
    color: "",
  },
  {
    img: "/images/insight.svg",
    svg: insight,
    svgName: "Insights",
    title: "Get dashboard insights",
    snippet: "You get to see an overview of how you spend and buy products.",
    buttonText: "Let’s get started",
    color: "bg-orange-25",
  },
]);

const quickStep = ref([
  {
    title: "Create an account",
    snippet: "Create an account for your business in less than 2minutes",
  },
  {
    title: "Add to cart with ease",
    snippet: "Add multiple items you want to buy in bulk in no time",
  },
  {
    title: "Checkout with ease",
    snippet: "Proceed to give us delivery informations and checkout very fast",
  },
]);
onMounted(() => {
  AOS.init({
    duration: 1300,
  });

  const lenis = new Lenis();

  lenis.on("scroll", (e) => {
    // console.log(e);
  });

  function raf(time) {
    lenis.raf(time);
    requestAnimationFrame(raf);
  }

  requestAnimationFrame(raf);
});
</script>

<style scoped>
.client {
  width: 100%;
  display: flex;
  flex-direction: column;
  align-items: center;
  gap: 32px;
}

.client h3 {
  font-size: 24px;
}

.logos {
  width: 100%;
  display: flex;
  justify-content: space-between;
  align-items: center;
}
.bfy-wrap {
  display: flex;
  align-items: flex-start;
  flex-wrap: wrap;
  justify-content: space-between;
  width: 100%;
  align-self: stretch;
  margin-inline: auto;
}

.feature-wrap {
  display: grid;
  grid-template-columns: repeat(12, 1fr);
  gap: 40px;
}

.feature-item1 {
  grid-column: 1 / span 8;
}
.feature-item2 {
  grid-column: 9 / 13;
}
.feature-item3 {
  grid-column: 1 / 7;
}
.feature-item4 {
  grid-column: 7 / 13;
}
.feature-item5 {
  grid-column: 1 / 5;
}
.feature-item6 {
  grid-column: 5 / 13;
}

.mt-128 {
  margin-top: 128px;
}
.img {
  width: 100%;
  height: 608px;
  border-radius: 24px;
  overflow: hidden;
  background-color: rgba(145, 214, 168, 1);
}

.img img {
  width: 100%;
  height: 100%;
  object-fit: cover;
}

@media (max-width: 960px) {
  .logos {
    flex-wrap: wrap;
    gap: 32px;
  }

  .logos img {
    max-width: 70px;
  }

  .feature-wrap {
    display: flex;
    flex-direction: column;
  }
  .bfy-wrap {
    justify-content: center;
    gap: 48px;
  }
  .client h3 {
    font-size: 20px;
    line-height: 30px; /* 150% */
    letter-spacing: -0.3px;
  }
  .img img {
    object-position: right 80% bottom 0px;
  }
}

@media (max-width: 700px) {
  .feature-wrap {
    gap: 20px;
  }

  .mt-128 {
    margin-top: 48px;
  }
}
</style>
