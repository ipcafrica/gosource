<template>
  <div class="wrapper">
    <nav :class="{ active: active }">
      <div class="logo-menu">
        <div class="logo">
          <Logo />
        </div>
        <ul>
          <li style="height: 56px; margin-bottom: 7px;">
            <Logo />
            <div class="close-icon" @click="handleMenu()">
              <div class="x-line"></div>
              <div class="x-line"></div>
            </div>
          </li>
          <li v-for="(data, index) in navData" :key="index">
            <nuxt-link
              :to="data.link"
              class="base-font text-body-large-medium medium text-grey-700"
              >{{ data.title }}</nuxt-link
            >
            <div v-html="caretRight"></div>
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
    <div class="bg-overlay"></div>
  </div>
</template>

<script setup>
import { caretRight, cancel } from "../utils/svg";
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

ul li {
  display: flex;
  justify-content: space-between;
  align-items: center;
  align-self: stretch;
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
.active + .bg-overlay {
  position: fixed;
  width: 100%;
  height: 100vh;
  background: #ff000000;
  top: 0;
  z-index: -1;
}
.close-icon {
  display: inline-block;
  position: relative;
  width: 20px;
  height: 20px;
  cursor: pointer;
}

.close-icon .x-line {
  position: absolute;
  top: 50%;
  left: 50%;
  width: 16px;
  height: 1.5px;
  border-radius: 6px;
  background-color: #333;
  transform-origin: center;
}

.close-icon .x-line:nth-child(1) {
  transform: translate(-50%, -50%) rotate(45deg);
}

.close-icon .x-line:nth-child(2) {
  transform: translate(-50%, -50%) rotate(-45deg);
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
  .active ul {
    position: fixed;
    top: 50px;
    left: 50%;
    transform: translateX(-50%);
    display: flex;
    height: auto;
    padding: 0px 16px 32px 16px;
    flex-direction: column;
    align-items: center;
    gap: 39px;
    border-radius: 12px;
    border: 1px solid var(--Grey-200);
    background: var(--White);
    z-index: 9;

    /* Shadow/Shadow__XXLarge */
    box-shadow: 0px 25px 50px 0px rgba(71, 83, 103, 0.25);
  }
  .cta .w-auto:first-child,
  .cta .w-auto:nth-child(2) {
    display: none;
  }
}
</style>
