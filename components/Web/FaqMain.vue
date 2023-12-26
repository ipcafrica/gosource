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
        header: 'Do you offer customized or specialty items upon request?',
        content: "Yes, we specialize in providing customized and specialty items tailored to your restaurant's specific needs. Feel free to inquire about any unique requirements."
    },
    {   
        id: 2,
        header: 'What are your delivery times and shipping costs?',
        content: 'Our delivery times vary based on location and order specifics. Shipping costs are calculated based on order size. We aim for timely deliveries and competitive shipping rates.'
    },
    {
        id: 3,
        header: 'What is your return or exchange policy if we receive damaged or incorrect items?',
        content: "In case of damaged or incorrect items, please notify us immediately. We have a hassle-free return and exchange policy. We'll arrange for replacements or refunds as per your preference."
    },
    {
        id: 4,
        header: 'How do you handle backorders or items out of stock?',
        content: "If an item is out of stock or on backorder, we'll promptly inform you and provide estimated restocking dates. You can choose to wait or make alternative arrangements."
    },
    {
        id: 5,
        header: 'Is there a dedicated account manager or point of contact for our restaurant?',
        content: 'Yes, we assign a dedicated account manager to each restaurant to ensure personalized service and smooth communication for all your needs.'
    },
    {
        id: 6,
        header: 'What payment methods do you accept?',
        content: 'We accept various payment methods, including credit/debit cards, bank transfers, and other secure online payment options for your convenience.'
    },
    {
        id: 7,
        header: 'Can you assist with sourcing rare or hard-to-find ingredients/products?',
        content: 'Absolutely, we have extensive networks and expertise to assist in sourcing rare or hard-to-find ingredients/products. Just let us know your requirements.'
    },
    {
        id: 8,
        header: 'What types of credit facilities do you offer for restaurants?',
        content: 'We offer diverse credit facilities, tailored to restaurant needs.'
    },
    {
        id: 9,
        header: 'What are the eligibility criteria for obtaining a credit facility?',
        content: 'Eligibility criteria typically involve factors like credit history, business revenue, and time in operation. Our team will guide you through the specific requirements.'
    },
    {
        id: 10,
        header: 'What is the maximum/minimum credit limit available?',
        content: 'The credit limits vary based on several factors. We assess your needs and financial situation to determine the most suitable credit limit for your restaurant.'
    },
    {
        id: 11,
        header: 'What are the interest rates or fees associated with the credit facility?',
        content: 'Interest rates and fees depend on the type of credit facility and individual circumstances. Our team will provide transparent information on rates and fees applicable to your chosen facility.'
    },
    {
        id: 12,
        header: 'Do you offer flexible repayment options or schedules?',
        content: "Yes, we understand the importance of flexibility. We offer various repayment options and schedules tailored to accommodate your restaurant's cash flow and needs."
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