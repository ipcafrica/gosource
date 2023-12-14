<template>
<div class="accordion">
  <div class="accordio-header">
    <h4 class="text-heading-4-medium medium text-grey-700"> {{ item.header }} </h4>
  </div>
  <div class="accordion-content " :class="{'open': isOpen}">
            <p class="text-body-large-regular regular text-grey-900-base">{{ item.content }}</p>
        </div>
</div>
</template>


<script setup>
import { ref, watch, onMounted, defineProps, defineEmits } from 'vue';
const props = defineProps({
  item:{
    type: Object,
    required: true
  },
  activeId:{
    type: number,
    required: true
  }
})
</script>

<style scoped>

</style>