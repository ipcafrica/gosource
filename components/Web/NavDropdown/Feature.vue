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
  margin-top: 16px;
  display: flex;
  padding: 0px 8px;
  flex-direction: column;
  align-items: flex-start;
  gap: 16px;
  align-self: stretch;
}
.svg-group {
  display: flex;
  align-items: center;
  gap: 16px;
}

.content {
  display: flex;
  flex-direction: column;
  align-items: flex-start;
  gap: 2px;
}
</style>
