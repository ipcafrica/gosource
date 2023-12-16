<template>
  <div class="wrapper">
    <nav>
      <div class="logo-menu">
        <div class="logo">
          <Logo />
        </div>
        <ul>
          <li v-for="(data, index) in navData" :key="index">
            <nuxt-link
              :to="data.link"
              class="base-font text-body-large-medium medium text-grey-700"
              >{{ data.title }}</nuxt-link
            >
          </li>
        </ul>
      </div>
      <div class="cta">
        <DynamicButtonMain
          buttonText="Log in"
          size="medium"
          type="link-neutral"
          class="w-auto"
        />
        <DynamicButtonMain
          buttonText="Sign up"
          size="medium"
          type="filled"
          class="w-auto"
        />

        <DynamicButtonMain
          buttonText="Sign up"
          size="small"
          type="filled"
          class="w-auto cta-mobile"
        />
        <div class="menu" :class="{ active: active }" @click="handleMenu()">
          <span></span>
          <span></span>
          <span></span>
        </div>
      </div>
    </nav>
  </div>
</template>

<script setup>
import { ref } from "vue";

defineProps({
  navData: {
    type: Array,
    required: true,
  },
});
const active = ref(false);
const handleMenu = () => {
  active.value = !active.value;
};
</script>

<style scoped>
.cta-mobile {
  display: none;
}
.wrapper {
  position: sticky;
  top: 0;
  background: var(--White);
  z-index: 999;
}
nav {
  display: flex;
  max-width: 80%;
  width: 100%;
  margin-inline: auto;
  padding: 16px 0;
  justify-content: space-between;
  align-items: center;
  gap: 40px;
}
.logo-menu {
  display: flex;
  max-width: 508.525px;
  width: 100%;
  height: 24px;
  justify-content: center;
  align-items: center;
  gap: 56px;
}
ul,
li {
  list-style: none;
}
ul {
  display: flex;
  max-width: 332px;
  width: 100%;
  height: 24px;
  justify-content: space-between;
  align-items: center;
  gap: 16px;
  flex-shrink: 0;
}
.cta {
  display: flex;
  align-items: center;
  gap: 24px;
}
.menu {
  position: relative;
  display: flex;
  align-items: center;
  flex-direction: column;
  gap: 4px;
  padding: 2px;
  width: 24px;
}
.menu.active {
  height: 24px;
}
.menu span {
  width: 22px;
  height: 2px;
  background: var(--grey-700);
  border-radius: 4px;
  transition: all calc(var(--animation-duration) / 3) linear;
}
.menu.active span {
  position: absolute;
}
.active span:nth-child(1) {
  top: 8px;
  left: 1px;
  width: 14px;
  rotate: 45deg;
}
.active span:nth-child(2) {
  rotate: -45deg;
  top: 11px;
  right: 0;
  width: 24px;
}
.active span:nth-child(3) {
  bottom: 7px;
  right: 1px;
  width: 14px;
  rotate: 45deg;
}
@media (max-width: 950px) {
  .cta-mobile {
    display: block;
  }
  .logo-menu {
    width: auto;
    max-width: auto;
  }
  ul {
    display: none;
  }
  .cta .w-auto:first-child, 
  .cta .w-auto:nth-child(2) {
    display: none;
  }
}
</style>
