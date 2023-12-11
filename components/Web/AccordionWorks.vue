<template>
    <div class="dynamic-accordion">
      <Accordion
        v-for="item in accordionData"
        :key="item.id"
        :item="item"
        @toggleAccordion="toggleAccordion($event)"
      />
    </div>
  </template>
  
  <script setup>
  import Accordion from './Accordion.vue';
  import { ref } from 'vue';
  
  const accordionData = ref([
  { id: 1, title: 'How do I sign up?', content: 'Content for Item 1', isOpen: false },
    { id: 2, title: 'Can individuals use this service?', content: 'Content for Item 2', isOpen: false },
    { id: 3, title: 'How does GoSource work?', content: 'Content for Item 3', isOpen: false },
    { id: 4, title: 'How much credit am I eligible for?', content: 'Content for Item 4', isOpen: false },
    { id: 5, title: 'How do I access credit?', content: 'Content for Item 5', isOpen: false },
  ]);
  
  
  const toggleAccordion = (e) => {
    if (e) {
    accordionData.value = accordionData.value.map((accItem) => ({
      ...accItem,
      isOpen: accItem.id === e ? !accItem.isOpen : false,
    }));
  }
console.log(e)
}
  </script>
  
  <style scoped>
  /* Add your custom accordion styles and animations here */
  .dynamic-accordion {
    max-width: 100%; /* Adjust the width as needed */
    display: flex;
    flex-direction: column;
    justify-content: center;
    align-items: center;
  }
  
  /* Add any other styles you need for the accordion items */
  </style>
  