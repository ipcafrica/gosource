<template>
  <div class="tag-wrapper">
    <slot name="svg" />
    <p class="text-body-micro-bold bold">Insights</p>
  </div>
</template>

<script>
export default {};
</script>

<style scoped>
.tag-wrapper {
  display: flex;
  height: 28px;
  padding: 0px 10px;
  justify-content: center;
  align-items: center;
  gap: 8px;
}
</style>
