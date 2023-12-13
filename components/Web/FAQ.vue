<template>
  <div class="accordion">
    <div
      v-for="(content, index) in accordionContent"
      :key="index"
      class="accordion-content"
      :class="{ open: content.open }"
    >
      <header @click="toggleAccordion(index)">
        <span class="title">{{ content.title }}</span>
        <i :class="content.open ? 'fas fa-minus' : 'fas fa-plus'"></i>
      </header>
      <p class="description" v-show="content.open">
        {{ content.description }}
      </p>
    </div>
  </div>
</template>

<script setup>
import { ref } from "vue";

const accordionContent = ref([
  {
    title: "What do you mean by Accordion?",
    description: "Lorem ipsum, ...",
    open: false,
  },
  {
    title: "What do you mean by Accordion?",
    description: "Lorem ipsum, ...",
    open: false,
  },
  {
    title: "What do you mean by Accordion?",
    description: "Lorem ipsum, ...",
    open: false,
  },
  {
    title: "What do you mean by Accordion?",
    description: "Lorem ipsum, ...",
    open: false,
  },
]);

const toggleAccordion = (index) => {
  accordionContent.value.forEach((item, i) => {
    if (i === index) {
      item.open = !item.open; // Toggle the clicked item
    } else {
      item.open = false; // Close all other items
    }
  });
};
</script>

<style scoped>
.accordion {
  max-width: 530px;
  width: 100%;
  background: #fff;
  margin: 0 15px;
  padding: 15px;
  border-radius: 8px;
  box-shadow: 0 0 4px rgba(0, 0, 0, 0.2);
}
.accordion .accordion-content {
  margin: 10px 0;
  border-radius: 4px;
  background: #fff7f0;
  border: 1px solid #ffd6b3;
  overflow: hidden;
}
.accordion-content:nth-child(2) {
  background-color: #f0faff;
  border-color: #cceeff;
}
.accordion-content:nth-child(3) {
  background-color: #fff0f3;
  border-color: #ffccd6;
}
.accordion-content:nth-child(4) {
  background-color: #f0f0ff;
  border-color: #ccccff;
}
.accordion-content.open {
  padding-bottom: 10px;
}
.accordion-content header {
  display: flex;
  min-height: 50px;
  padding: 0 15px;
  cursor: pointer;
  align-items: center;
  justify-content: space-between;
  transition: all 0.2s linear;
}
.accordion-content.open header {
  min-height: 35px;
}
.accordion-content header .title {
  font-size: 14px;
  font-weight: 500;
  color: #333;
}
.accordion-content header i {
  font-size: 15px;
  color: #333;
}
.accordion-content .description {
  height: 0;
  font-size: 12px;
  color: #333;
  font-weight: 400;
  padding: 0 15px;
  transition: all 0.2s linear;
}

.accordion-content.open .description {
  height: auto;
}
</style>
