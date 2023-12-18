<template>
  <div class="accordion" :class="{ 'opened': isOpen, 'close': !isOpen }">
    <div class="accordion-header" @click="toggleAccordion">
      <h4 class="text-heading-4-medium medium text-grey-700 header">{{ item.header }}</h4>
      <WebPlusMinus :isOpen="isOpen" />
    </div>
    <div class="accordion-content" :class="{ 'open': isOpen }" ref="contentRef">
      <p class="text-body-large-regular regular text-grey-900-base title">{{ item.content }}</p>
    </div>
  </div>
</template>

<script setup>
import { ref, watch, onMounted, defineProps, defineEmits } from 'vue';

const props = defineProps(['item', 'activeId']);
const isOpen = ref(false);
const contentRef = ref(null);
const emits = defineEmits(['closeOtherAccordions']);

const toggleAccordion = () => {
  if (props.activeId !== props.item.id) {
    emits('closeOtherAccordions', props.item.id);
  }
  isOpen.value = !isOpen.value;
};

watch(() => props.activeId, (newActiveId) => {
  isOpen.value = newActiveId === props.item.id;
});

onMounted(() => {
  contentRef.value.style.transition = 'all 0.5s ease-in-out';
});

</script>

<style scoped>
.accordion {
  display: flex;
  flex-direction: column;
  align-items: flex-start;
  padding-bottom: 8px;
}

.accordion-header {
  padding: 24px 24px 16px 24px;
  width: 100%;
  cursor: pointer;
  display: flex;
  align-items: center;
  justify-content: space-between;
  text-align: left;
}

.accordion-content {
  height: 0px;
  padding: 0px 24px 0px 24px;
  text-align: left;
  overflow: hidden;
  transition: all 0.5s ease-in-out;
}

.open {
  height: 72px;
}

.opened {
  padding-bottom: 24px;
}

@media screen and (max-width: 1100px) {
  .open {
    height: 72px;
  }
}

@media screen and (max-width: 788px) {
  .open {
    height: 100px;
  }
}

@media screen and (max-width: 610px) {
  .open {
    height: 84px;
  }

  .header {
    font-size: 16px;
    font-style: normal;
    font-weight: 500;
    line-height: 24px;
    letter-spacing: -0.2px;
  }

  .title {
    font-size: 14px;
    font-style: normal;
    font-weight: 400;
    line-height: 21px;
    letter-spacing: -0.2px;
  }
}

@media screen and (max-width: 545px) {
  .open {
    height: 105px;
  }
}

@media screen and (max-width: 472px) {
  .open {
    height: 126px;
  }
}

@media screen and (max-width: 396px) {
  .open {
    height: 147px;
  }
}

@media screen and (max-width: 354px) {
  .open {
    height: 168px;
  }
}
</style>
