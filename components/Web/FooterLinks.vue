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
    <span>
      <svg
        xmlns="http://www.w3.org/2000/svg"
        width="17"
        height="17"
        viewBox="0 0 17 17"
        fill="none"
      >
        <path
          d="M13.5917 4.5V11C13.5917 11.1989 13.5127 11.3897 13.372 11.5303C13.2314 11.671 13.0406 11.75 12.8417 11.75C12.6428 11.75 12.452 11.671 12.3113 11.5303C12.1707 11.3897 12.0917 11.1989 12.0917 11V6.3125L5.3723 13.0306C5.23141 13.1715 5.04031 13.2507 4.84105 13.2507C4.6418 13.2507 4.4507 13.1715 4.3098 13.0306C4.16891 12.8897 4.08975 12.6986 4.08975 12.4994C4.08975 12.3001 4.16891 12.109 4.3098 11.9681L11.0292 5.25H6.34168C6.14277 5.25 5.952 5.17098 5.81135 5.03033C5.6707 4.88968 5.59168 4.69891 5.59168 4.5C5.59168 4.30109 5.6707 4.11032 5.81135 3.96967C5.952 3.82902 6.14277 3.75 6.34168 3.75H12.8417C13.0406 3.75 13.2314 3.82902 13.372 3.96967C13.5127 4.11032 13.5917 4.30109 13.5917 4.5Z"
          fill="#19B820"
        />
      </svg>
    </span>
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
  flex-direction: row;
  align-items: stretch;
  gap: 4px;
}

a {
  white-space: nowrap;
  letter-spacing: -0.2px;
  transition: all calc(var(--animation-duration)) ease;
}

span {
  position: relative;
}

span svg {
  position: absolute;
  top: 4px;
  left: -2px;
  opacity: 0;
  transition: all calc(var(--animation-duration)) ease;
}

.footer-link:hover a {
  color: var(--grey-900-base);
  font-weight: 500;
}
.footer-link:hover span svg{
  top: 3px;
  left: 0px;
  opacity: 1;
}
</style>
