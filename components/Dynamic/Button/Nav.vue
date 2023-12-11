<template>
  <NuxtLink :to="url">
    <slot name="svg"></slot>
    <div class="nav-text text-body-small-medium base-font">
      {{ buttonText }}
    </div>
  </NuxtLink>
</template>

<script setup>
defineProps({
  buttonText: {
    type: String,
  },
  url: {
    type: String,
  },
});
</script>

<style scoped>
a {
  text-decoration: none;
  cursor: pointer;
}
a {
  display: flex;
  width: 100%;
  height: 40px;
  padding: 16px 12px;
  flex-direction: column;
  justify-content: center;
  align-items: flex-start;

  transition: 0.3s;

  border-radius: 100px;
  background: var(--white);
}

.nav-text {
  color: var(--grey-700);
}
</style>


<style>
a:hover {
  background: var(--grey-100);
}

a.router-link-active.router-link-exact-active,
a.router-link-active,
a.router-link-exact-active {
  background: var(--supporting-supporting-500-base);
}
a.router-link-active.router-link-exact-active .nav-text {
  color: var(--white);
}

a.router-link-active.router-link-exact-active.nav-button svg,
a.router-link-active.nav-button svg,
a.router-link-exact-active.nav-button svg {
  background: var(--supporting-supporting-500-base);
}
</style>