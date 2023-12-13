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
            <svg
              xmlns="http://www.w3.org/2000/svg"
              width="20"
              height="20"
              viewBox="0 0 20 20"
              fill="none"
            >
              <path
                d="M7.45773 3.79223L7.45782 3.79232L7.45773 3.79223Z"
                fill="#344054"
                stroke="white"
                stroke-width="2"
              />
            </svg>
          </template>
        </DynamicButtonMain>
      </div>
      <div class="">
        <WebHeroSVG />
      </div>
    </div>
  </main>
</template>

<script>
export default {};
</script>

<style scoped>
main {
  padding-inline: 24px;
  display: flex;
  align-items: flex-end;
  max-width: 100%;
  height: 642px;
  background: var(--orange-orange-25);
}
.wrapper {
  width: fit-content;
  margin-inline: auto;
  display: flex;
  align-items: center;
}
.content-group {
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
</style>
