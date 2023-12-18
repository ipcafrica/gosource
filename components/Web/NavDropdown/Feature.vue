<template>
  <div class="drop-wrap">
    <div class="" v-for="(data, index) in data" :key="index">
      <div class="svg-group">
        <div v-html="data.svg"></div>
        <div class="content">
          <p class="body-small-medium medium text-grey-900-base">{{ data.title }}</p>
          <p class="body-small-regular regular text-grey-500">{{ data?.snippet }}</p>
        </div>
      </div>
    </div>
  </div>
</template>

<script setup>
defineProps({
  data: {
    type: Array,
  },
});
</script>

<style scoped>
.drop-wrap {
  position: absolute;
  margin-top: 12px;
  display: flex;
  padding: 12px;
  flex-direction: column;
  align-items: flex-start;
  gap: 8px;
  max-width: 420px;
  width: 100%;

  border-radius: 16px;
  border: 1px solid var(--grey-200);
  background: var(--White);

  /* Shadow/Shadow__XXLarge */
  box-shadow: 0px 25px 50px 0px rgba(71, 83, 103, 0.25);
}
.svg-group {
  display: flex;
padding: 12px;
align-items: center;
gap: 16px;
align-self: stretch;
}

.content {
  display: flex;
  flex-direction: column;
  align-items: flex-start;
  gap: 2px;
}

@media (max-width: 950px) {
  .drop-wrap {
    position: relative;
    margin-top: 16px;
    padding: 0px 8px;
    flex-direction: column;
    gap: 16px;
  }
  .svg-group {
    padding: 0;
  }
}
</style>
