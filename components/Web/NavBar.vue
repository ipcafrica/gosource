<template>
  <div>
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
      </div>
    </nav>
  </div>
</template>

<script setup>
defineProps({
  navData: {
    type: Array,
    required: true,
  },
});
</script>

<style scoped>
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
</style>
