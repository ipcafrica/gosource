<template>
  <main>
    <div class="wrapper">
      <div class="content-group">
        <h1>Enjoy a Hassle-Free hustle.</h1>
        <p>
          GoSource is a strong force in food sourcing and delivery, lifting
          responsibilities from businesses and consumers to keep the supply chain smooth.
        </p>
        <DynamicButtonMain
          size="medium"
          type="primary"
          icon="icon-right"
          buttonText="Get started"
          class="w-auto"
        >
          <template v-slot:svg>
            <div v-html="caretRightWhite"></div>
          </template>
        </DynamicButtonMain>
      </div>
      <WebHeroSVG class="svg" />
    </div>
  </main>
</template>

<script setup>
import { caretRightWhite } from "../utils/svg";
</script>

<style scoped>
main {
  padding-inline: 24px;
  display: flex;
  align-items: flex-end;
  max-width: 100%;
  min-height: 642px;
  background: var(--orange-orange-25);
}
.wrapper {
  width: fit-content;
  margin-inline: auto;
  display: flex;
  flex-wrap: wrap;
  justify-content: center;
}
.content-group {
  margin-top: 28px;
  display: flex;
  max-width: 610px;
  margin-inline: auto;
  flex-direction: column;
  align-items: flex-start;
  gap: 24px;
}

h1 {
  color: var(--grey-900-base);
  font-size: 88px;
  font-style: normal;
  font-weight: 500;
  line-height: 100px; /* 113.636% */
  letter-spacing: -3px;
}

p {
  color: var(--grey-700);
  font-size: 20px;
  font-weight: 300;
  line-height: 30px; /* 150% */
  letter-spacing: -0.3px;
}
@media (max-width: 1181px) {
  .wrapper {
    flex-direction: column;
    gap: 64px;
  }
  .svg {
    width: 100%;
  }
}
@media (max-width: 900px) {
  .content-group {
    margin-top: 72px;
  }
  h1 {
    font-size: 48px;
    line-height: 64px; /* 133.333% */
    letter-spacing: -2px;
  }

  p {
    font-size: 16px;
    line-height: 24px; /* 150% */
    letter-spacing: -0.2px;
  }
}
</style>
