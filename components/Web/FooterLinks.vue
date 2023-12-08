<template>
  <div class="footer-link">
    <template v-if="type === 'mail'">
      <a
        :href="'mailto:' + text"
        class="base-font text-body-small-regular regular --bg-grey-700"
        >{{ text }}</a
      >
    </template>
    <template v-else-if="type === 'number'">
      <a
        :href="'tel:' + text"
        class="base-font text-body-small-regular regular --bg-grey-700"
        >{{ text }}</a
      >
    </template>
    <template v-else>
      <NuxtLink
        :to="link"
        class="base-font text-body-small-regular regular --bg-grey-700"
        >{{ text }}</NuxtLink
      >
    </template>
    <span></span>
  </div>
</template>

<script setup>
defineProps({
  text: {
    type: String,
    required: true,
  },
  link: {
    type: String,
  },
  type: {
    type: String,
    default: "normal", // Default type is 'normal'
  },
});
</script>

<style scoped>
.footer-link {
  display: flex;
  flex-direction: column;
  gap: 1px;
  width: fit-content;
}

a {
  white-space: nowrap;
  letter-spacing: -0.2px;
  transition: all var(--animation-duration) ease-in-out;
}

span {
  height: 2px;
  width: 0%;
  border-radius: 4px;
  background: var(--primary-primary-500-base);
  transition: all var(--animation-duration) ease-in-out;
}

.footer-link:hover a {
  color: var(--primary-primary-500-base);
}
.footer-link:hover span {
  width: 100%;
}
</style>
