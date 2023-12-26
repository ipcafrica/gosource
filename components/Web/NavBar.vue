<template>
  <div class="wrapper" :class="{ active: active }">
    <nav>
      <div class="logo-menu">
        <div class="logo">
          <Logo />
        </div>
        <ul>
          <li style="height: 56px; margin-bottom: 7px" class="mobile-logo">
            <div class="nav-menu">
              <Logo />
              <div class="close-icon" @click="toggleActive()">
                <div class="x-line"></div>
                <div class="x-line"></div>
              </div>
            </div>
          </li>
          <!-- <li
            v-for="(data, index) in navData"
            :key="index"
            @click="toggleDropdown(data.title)"
            @mouseleave="toggleDropdownHoverLeave(data.title)"
            @mouseover="toggleDropdownHover(data.title)"
          > -->
          <li
            v-for="(data, index) in navData"
            :key="index"
            @click="toggleDropdownClick(data.title)"
            @mouseover="toggleDropdown(data.title)"
          >
            <div class="nav-menu">
              <nuxt-link
                :to="data.link"
                v-if="data.link"
                class="base-font text-body-large-medium medium text-grey-700"
              >
                {{ data.title }}
              </nuxt-link>
              <div
                class="base-font text-body-large-medium medium text-grey-700"
                v-if="!data.link"
              >
                {{ data.title }}
              </div>
              <div
                v-if="data.dropdown"
                v-html="caretRight"
                class="mobile-logo caretRight"
                :class="{
                  open:
                    (feature && data.title === 'Features') ||
                    (company && data.title === 'Company'),
                }"
              ></div>
            </div>
            <WebNavDropdownFeature
              class="mobile-logo"
              :class="{ feature: feature }"
              :data="data.dropdown"
              v-if="feature && data.title === 'Features'"
            />
            <WebNavDropdownCompany
              class="mobile-logo"
              :class="{ company: company }"
              :data="data.dropdown"
              v-if="company && data.title === 'Company'"
            />
          </li>
          <div class="cta mobile-logo">
            <DynamicButtonMain buttonText="Sign up" size="medium" type="filled" />
            <DynamicButtonMain buttonText="Log in" size="medium" type="link-neutral" />
          </div>
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
        <div class="menu" :class="{ active: active }" @click="toggleActive()">
          <span></span>
          <span></span>
          <span></span>
        </div>
      </div>
    </nav>
    <div
      class="bg-overlay"
      :class="{ feature: feature, company: company }"
      @mouseover="closeDropdown"
    ></div>
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
const feature = ref(false);
const company = ref(false);

const toggleActive = () => {
  active.value = !active.value;
};
const toggleDropdown = (arg) => {
  // console.log(arg);
  switch (arg) {
    case "Features":
      feature.value = true;
      // feature.value = !feature.value;
      company.value = false;
      break;
    case "Company":
      company.value = true;
      // company.value = !company.value;
      feature.value = false;
      break;
    default:
      feature.value = false;
      company.value = false;
      break;
  }
};

const toggleDropdownClick = (arg) => {
// console.log(arg);
switch (arg) {
    case "Features":
      feature.value = !feature.value;
      company.value = false;
      break;
    case "Company":
      company.value = !company.value;
      feature.value = false;
      break;
    default:
      feature.value = false;
      company.value = false;
      break;
  }
}

const closeDropdown = () => {
  feature.value = false;
  company.value = false;
};
const toggleDropdownHoverLeave = (arg) => {
  // console.log(arg);
  // switch (arg) {
  //   case "Features":
  //     feature.value = false;
  //     // company.value = false;
  //     break;
  //   case "Company":
  //     company.value = false;
  //     // feature.value = false;
  //     break;
  //   default:
  //     feature.value = false;
  //     company.value = false;
  //     break;
  // }
};
const toggleDropdownHover = (arg) => {
  // console.log(arg);
  // switch (arg) {
  //   case "Features":
  //     feature.value = true;
  //     company.value = false;
  //     break;
  //   case "Company":
  //     company.value = true;
  //     feature.value = false;
  //     break;
  //   default:
  //     feature.value = false;
  //     company.value = false;
  //     break;
  // }
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

ul li .nav-menu {
  cursor: pointer;
  width: 100%;
  display: flex;
  justify-content: space-between;
  align-items: center;
  gap: 8px;
  align-self: stretch;
}
.cta {
  display: flex;
  align-items: center;
  gap: 24px;
}
.menu {
  position: relative;
  display: none;
  align-items: center;
  flex-direction: column;
  gap: 4px;
  padding: 2px;
  width: 24px;
}
.mobile-logo {
  display: none;
}
.menu.active {
  height: 24px;
  display: none;
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
  background: rgba(255, 255, 255, 0);
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
  background-color: var(--grey-700);
  transform-origin: center;
}

.close-icon .x-line:nth-child(1) {
  transform: translate(-50%, -50%) rotate(45deg);
}

.close-icon .x-line:nth-child(2) {
  transform: translate(-50%, -50%) rotate(-45deg);
}

.caretRight {
  transition: all calc(var(--animation-duration) / 2) ease;
}

.open {
  rotate: 90deg;
}

.mobile-logo.feature {
  display: flex;
}
.mobile-logo.company {
  display: flex;
}

.bg-overlay.feature,
.bg-overlay.company {
  position: absolute;
  height: 100vh;
  background: none;
  width: 100%;
  z-index: -1;
}

@media (max-width: 950px) {
  ul {
    max-width: 90%;
    overflow-y: auto;
  }
  .menu {
    display: flex;
  }
  .active .mobile-logo {
    display: flex;
  }
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
    position: absolute;
    top: 14px;
    left: 50%;
    transform: translateX(-50%);
    display: flex;
    /* max-height: 90vh; */
    height: auto;
    padding: 0px 16px 32px 16px;
    flex-direction: column;
    align-items: center;
    gap: 39px;
    border-radius: 12px;
    border: 1px solid var(--grey-200);
    background: var(--White);
    z-index: 9;
    scrollbar-width: thin; /* For Firefox */
    scrollbar-color: transparent transparent; /* For Firefox */
    -ms-overflow-style: none; /* For Internet Explorer and Edge */

    /* Shadow/Shadow__XXLarge */
    box-shadow: 0px 25px 50px 0px rgba(71, 83, 103, 0.25);
  }
  ::-webkit-scrollbar {
    width: 1px; /* Adjust the width as needed */
    background: white !important;
  }

  .active ul::-webkit-scrollbar-thumb {
    background-color: transparent;
  }
  .cta .w-auto:first-child,
  .cta .w-auto:nth-child(2) {
    display: none;
  }

  ul .cta {
    flex-direction: column;
    width: 100%;
  }

  li {
    width: 100%;
  }

  .wrapper.active {
    position: relative;
  }
}
@media (max-width: 364px) {
  .cta .w-auto:nth-child(3) {
    display: none;
  }
}
</style>
