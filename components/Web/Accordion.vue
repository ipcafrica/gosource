<template>
    <div class="accordion-item" :class="{ 'active': item.isOpen }">
      <div class="accordion-header" @click="$emit('toggleAccordion', item.id)">
        <h4 class="text-heading-4-medium medium text-grey-700">{{ item.title }}</h4>
        <PlusMinusIcon :isOpen="item.isOpen"/>
      </div>
      <div class="accordion-content" v-show="item.isOpen" :class="{ 'open-animation': item.isOpen }">
        {{ item.content }}
      </div>
    </div>
  </template>
  
  <script setup>
  import PlusMinusIcon from './PlusMinusIcon.vue';
  const { item } = defineProps({
    item: {
        type: Object
    }
  });
//   const toggleAccordion = () => emit('toggleAccordion', item.id)
  </script>
  
  <style scoped>
  /* Add your custom accordion item styles and animations here */
  .accordion-item {
    padding: 24px;
    max-width: 100%;
    width:100%;
    display: flex;
    /* justify-content: center; */
    align-items: center;
}
  
  .accordion-header {
    cursor: pointer;
    /* padding: 10px; */
    background-color: var(--white);
    display: flex;
    align-items: center;
    justify-content: space-between;
    width: 100%;
  }
  
  .accordion-content {
    padding: 10px;
    border: 1px solid var(--white);
    max-height: 0;
    overflow: hidden;
    transition: max-height 0.5s ease-out; /* Add your animation properties */
  }
  
  .active .accordion-header {
    background-color: var(--white);
  }
  
  .open-animation {
    max-height: 500px; /* Adjust the max-height based on your content */
  }
  </style>
  