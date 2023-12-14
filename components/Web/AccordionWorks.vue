<template>
  <div class="accordion-content">
      <Accordion v-for="(item, index) in accordionData" :key="index" :item="item"
      :activeId="activeId"
      />
  </div>
</template>

<script setup>
import {ref} from 'vue'
const accordionData = ref([
    {
        id: 1,
        header: 'Accordion Item 1',
        content: 'Lorem ipsum dolor sit amet consectetur, adipisicing elit. Dicta et beatae officiis ipsum pariatur magnam aliquam maxime, error nesciunt sed, eaque eius, suscipit voluptas harum!'
    },
    {   
        id: 2,
        header: 'Accordion Item 2',
        content: 'Lorem ipsum dolor sit amet consectetur, adipisicing elit. Dicta et beatae officiis ipsum pariatur magnam aliquam maxime, error nesciunt sed, eaque eius, suscipit voluptas harum!'
    },
    {
        id: 3,
        header: 'Accordion Item 3',
        content: 'Lorem ipsum dolor sit amet consectetur, adipisicing elit. Dicta et beatae officiis ipsum pariatur magnam aliquam maxime, error nesciunt sed, eaque eius, suscipit voluptas harum!'
    },
    {
        id: 4,
        header: 'Accordion Item 4',
        content: 'Lorem ipsum dolor sit amet consectetur, adipisicing elit. Dicta et beatae officiis ipsum pariatur magnam aliquam maxime, error nesciunt sed, eaque eius, suscipit voluptas harum!'
    }
])
const activeId = ref(null);
</script>

<style scoped>

</style>