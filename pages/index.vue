<template>
  <div>
    <WebNews />
    <WebHero />
    <!-- logo -->
    <WebSection :data="null">
      <template v-slot:content>
        <div class="client">
          <h3 class="heading-3-medium medium text-grey-900">
            Trusted by 100+ businesses across the Nation
          </h3>
          <div class="logos">
            <img :src="image" alt="" v-for="(image, index) in images" :key="index" />
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
      >
        <template v-slot:content>
          <div class="feature-wrap mt-128">
            <div
              v-for="(data, index) in featureCardData"
              :key="index"
              :class="'feature-item' + (index + 1)"
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
    <WebSection :data="sectionData[1]" flexPosition="center" maxWidth="458px" left="left">
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
    <!-- Quick steps -->
    <div class="">
      <WebSection :data="sectionData[2]" flexPosition="center">
        <template v-slot:content>
          <WebQuickStep class="mt-128" :data="quickStep" />
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
      >
        <template v-slot:content>
          <div class="img mt-128">
            <img src="/assets/images/zero-stress.png" alt="" />
          </div>
        </template>
      </WebSection>
    </div>

    <!-- testimonials here -->
    <!-- FAQ -->
    <WebSection :data="sectionData[4]" flexPosition="center">
      <template v-slot:content>
        <WebFAQ />
        <div class="accordion">
          <WebFaqMain/>
        </div>
      </template>
    </WebSection>
    <!-- Let’s go! -->
    <div class="bg-grey-50">
      <WebSection :data="sectionData[5]" flexPosition="center" maxWidth="458px" />
    </div>
    <WebFooter />
  
    <!-- <WaitlistSuccess-page @cliclickButton="nextModal"/> -->
    <WebTestimonial />
    <p ref="text" class="animated-text">
      <span v-for="(letter, index) in lettersArray" :key="index" :style="{ color: letter.color }">
        {{ letter.value }}
      </span>
    </p>
  </div>
</template>

<script setup>
import { ref, onMounted } from "vue";

const snippet = ref(
  "We no longer have to deal with multiple suppliers or chasing people with phone calls to supply us on time. Take take out orders and we expect delivery within 24 hours. The service and experience is brilliant."
);

const lettersArray = ref([]);

onMounted(() => {
  splitTextIntoLetters();
});

const splitTextIntoLetters = () => {
  const text = snippet.value;
  const textArray = text.split("");

  lettersArray.value = textArray.map((letter, index) => ({
    value: letter,
    color: "var(--grey-500)", // Initial color, you can adjust this
  }));

  animateText();
}

function animateText() {
  let index = 0;

  function updateColor() {
    lettersArray.value[index].color = "var(--grey-900-base)";
  }

  function animate() {
    if (index < lettersArray.value.length) {
      updateColor();
      index++;
      setTimeout(animate, 100); // Adjust the delay as needed
    }
  }

  animate();
}
</script>

<style scoped>
.animated-text span {
  font-size: 48px;
  transition: all 0.2s ease;
}
</style>
