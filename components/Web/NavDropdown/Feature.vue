<template>
  <div class="drop-wrap">
    <div class="dropdown-list" v-for="(data, index) in data" :key="index">
      <div class="svg-group">
        <div v-html="data.svg"></div>
        <div class="content">
          <p class="body-small-medium medium text-grey-900-base">{{ data.title }}</p>
          <p class="body-small-regular regular text-grey-500">{{ data?.snippet }}</p>
        </div>
      </div>
        <div class="icon" v-html="arrowRightUp"></div>
    </div>
  </div>
</template>

<script setup>
import { arrowRightUp } from "../utils/svg";
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


.icon {
  padding-right: 10px;
  opacity: 0;
  margin-top: 10px;
  transition: all var(--animation-duration) ease;
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


.dropdown-list {
  width: 100%;
  cursor: pointer;
  display: flex;
  align-items: center;
  justify-content: space-between;
  gap: 8px;
  border-radius: 10px;
  transition: all var(--animation-duration) ease;
}

.dropdown-list:hover {
  background: var(--grey-75);
}

.dropdown-list:hover .icon {
  opacity: 1;
  margin-top: 0;
}

@media (max-width: 950px) {
  .drop-wrap {
    position: relative;
    margin-top: 16px;
    padding: 0px 8px;
    flex-direction: column;
    gap: 16px;
    border: none;
    box-shadow: none;
    max-width: 100%;
  }
  .svg-group {
    padding: 0;
  }
  
  .dropdown-list {
    padding: 12px;
  }
}
</style>
