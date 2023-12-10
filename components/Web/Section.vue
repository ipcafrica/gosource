<template>
  <section class="section-wrapper">
    <div class="header-content">
      <header class="base-font">Hassle-Free</header>
      <div class="content">
        <h1 class="text-heading-1-medium medium text-grey-900-base">
          Let’s manage your procurement process
        </h1>
        <p class="text-body-large-regular regular text-grey-700">
          We are a food procurement, supply-chain, and logistics powerhouse that take
          responsibilities off businesses and consumers and keeps the supply chain
          running.
        </p>
      </div>
      <!-- <DynamicButton /> -->
    </div>
    <slot name="content" />
  </section>
</template>

<script setup></script>

<style scoped>
.section-wrapper {
  display: flex;
  max-width: 1440px;
  width: 80%;
  padding: 96px 150px;
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
</style>
