<template>
    <div class="accordion-content">
        <WebFaqItem v-for="(item, index) in accordionData" :key="index" :item="item"
        :activeId="activeId"
        @closeOtherAccordions="closeOtherAccordions"
        />
    </div>
</template>


<script setup>
// import FaqItem from '@/components/Web/FaqItem.vue'
import { ref } from 'vue';
const accordionData = ref([
    {
        id: 1,
        header: 'How do I sign up?',
        content: 'In the dynamic landscape of modern business, the demand for streamlined and efficient processes has never been more critical. One area that often faces complexities is food procurement, supply-chain management, and logistics.'
    },
    {   
        id: 2,
        header: 'Can individuals use this service?',
        content: 'In the dynamic landscape of modern business, the demand for streamlined and efficient processes has never been more critical. One area that often faces complexities is food procurement, supply-chain management, and logistics.'
    },
    {
        id: 3,
        header: 'How does GoSource work?',
        content: 'In the dynamic landscape of modern business, the demand for streamlined and efficient processes has never been more critical. One area that often faces complexities is food procurement, supply-chain management, and logistics.'
    },
    {
        id: 4,
        header: 'How much credit am i eligible for?',
        content: 'In the dynamic landscape of modern business, the demand for streamlined and efficient processes has never been more critical. One area that often faces complexities is food procurement, supply-chain management, and logistics.'
    },
    {
        id: 5,
        header: 'How do I access credit?',
        content: 'In the dynamic landscape of modern business, the demand for streamlined and efficient processes has never been more critical. One area that often faces complexities is food procurement, supply-chain management, and logistics.'
    }
])
const activeId = ref(null);


const closeOtherAccordions = (clickedId) => {
    activeId.value = activeId.value === clickedId ? null : clickedId;
    console.log(activeId.value)
};
</script>


<style scoped>
.accordion-content {
    /* border: 1px solid red; */
    display: flex;
    flex-direction: column;
    /* gap: 20px; */
    justify-content: center;
    align-items: center;


}
</style>