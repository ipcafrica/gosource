<template>
  <div class="wrapper">
    <div class="brand">
      <img :src="data.img" alt="" />
    </div>
    <div class="testimony base-font">{{ data.testimony }}</div>
    <div class="name">
      <h5 class="heading-5-edium medium text-grey-900-base">{{ data.name }}</h5>
      <p class="body-small-regular regular text-grey-500">{{ data.position }}</p>
    </div>
  </div>
</template>

<script setup>
defineProps({
  data: {
    type: Object,
    required: true,
  },
});
</script>

<style scoped>
.wrapper {
  display: flex;
  /* max-width: 1140px; */
  margin-inline: auto;
  width: 100%;
  flex-direction: column;
  align-items: center;
  gap: 48px;
}

.name {
  display: flex;
  flex-direction: column;
  align-items: center;
  gap: 2px;
}

.testimony {
  max-width: 823px;
  width: 100%;
  text-align: center;
  font-size: 34px;
  font-style: normal;
  font-weight: 500;
  line-height: 51px; /* 150% */
  letter-spacing: -1px;
}
@media (max-width: 960px) {
  .testimony {
    font-size: 20px;
    font-weight: 500;
    line-height: 30px; /* 150% */
    letter-spacing: -0.3px;
  }
}
</style>
