<template>
  <div class="drop-wrap">
    <div class="wrapper">
      <div class="wrap" v-for="(data, index) in data" :key="index">
        <div class="svg-group">
          <div v-html="data.svg"></div>
          <p class="body-small-medium medium text-grey-700">{{ data.title }}</p>
        </div>
      </div>
    </div>
    <div class="blog-wrap">
      <div class="img">
        <img src="/images/blog.png" alt="" />
      </div>
      <div class="content">
        <h6 class="heading-6-small-medium medium text-grey-700">Read our latest blog</h6>
        <p class="truncate">
          9 popular markets in Lagos you need to visit if you need to buy pocket-friendly
          foodstuffs Lagos is indubitably the commercial hub of Nigeria; it is a
          cosmopolitan metropolis that serves as a midpoint for trade, industrialization,
          and a financial paradise for food marketers.
        </p>
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
  margin-top: 12px;
  position: absolute;
  display: flex;
  max-width: 400px;
  width: 100%;
  padding: 12px;
  flex-direction: column;
  align-items: flex-start;
  gap: 40px;

  border-radius: 16px;
  border: 1px solid var(--Grey-100, #f0f2f5);
  background: var(--White, #fff);

  /* Shadow/Shadow__XXLarge */
  box-shadow: 0px 25px 50px 0px rgba(71, 83, 103, 0.25);
}

.svg-group {
  display: flex;
  align-items: center;
  gap: 8px;
  align-self: stretch;
}

.blog-wrap {
  width: 100%;
  display: flex;
  align-items: center;
  gap: 12px;
}

.wrapper {
  display: flex;
  flex-direction: row;
  align-items: flex-start;
  gap: 16px;
  flex-wrap: wrap;
}

.wrap {
  width: 47%;
}

.img {
  width: 48px;
  height: 48px;
}

.content {
  width: 70%;
  display: flex;
  flex-direction: column;
  align-items: flex-start;
  gap: 2px;
}

.truncate {
  max-width: 99%;
  white-space: nowrap;
  overflow: hidden;
  text-overflow: ellipsis;
  color: var(--grey-500);
  font-size: 12px;
  font-weight: 300;
  line-height: 18px;
}
@media (max-width: 950px) {
  .drop-wrap {
    position: relative;
    margin-top: 16px;
    padding: 0px 8px;
    gap: 24px;
  }

  .wrapper {
    flex-direction: column;
  }
}
</style>
