<template>
  <div class="card-wrapper">
    <div class="image-container"></div>
    <div class="content-container">
      <div class="tag">
      </div>
      <div class="text-group">
        <h2 class="text-heading-2-medium medium">All food items in one store</h2>
        <p class="text-body-large-regular regular">
          Buy all your quality food items in bulk in one store without going to the
          market.
        </p>
      </div>
      <div class="cta"></div>
    </div>
  </div>
</template>

<script>
export default {};
</script>

<style scoped>
.card-wrapper {
  display: flex;
  height: 608px;
  padding: 6px;
  flex-direction: column;
  align-items: center;
  justify-content: space-between;
  border-radius: 12px;
  border: 1px solid var(--grey-100);
  background: var(--White);

  /* Shadow/Shadow__Small */
  box-shadow: 0px 4px 8px 0px rgba(71, 83, 103, 0.1);
}

.content-container {
  display: flex;
  padding: 24px;
  flex-direction: column;
  align-items: flex-start;
  gap: 24px;
  border-radius: 8px;
  background: var(--White);
}
</style>
