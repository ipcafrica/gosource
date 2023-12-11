<template>
  <div class="card-wrapper">
    <div class="image-container">
      <img :src="data.img" alt="" />
    </div>
    <div class="content-container" v-if="data.title">
      <div class="tag" :class="data.color">
        <slot name="svg" />
        <div class="base-font text-body-micro-bold bold text-grey-900-base">
          {{ data.svgName }}
        </div>
      </div>
      <div class="text-group">
        <h2 class="text-heading-2-medium medium text-grey-900-base">{{ data?.title }}</h2>
        <p class="text-body-large-regular regular text-grey-700">
          {{ data?.snippet }}
        </p>
      </div>
      <div class="cta">
        <span class="base-font text-button-small medium text-grey-700">{{
          data.buttonText
        }}</span>
        <div class="hamburger is-active" id="hamburger-4">
          <span class="line"></span>
          <span class="line"></span>
          <span class="line"></span>
        </div>
      </div>
    </div>
  </div>
</template>

<script setup>
defineProps({
  data: {
    required: true,
  },
});
</script>

<style scoped>
.card-wrapper {
  position: relative;
  display: flex;
  height: 608px;
  width: auto;
  padding: 6px;
  flex-direction: column;
  align-items: center;
  justify-content: space-between;
  border-radius: 12px;
  border: 1px solid var(--grey-100);
  background: var(--White);

  /* Shadow/Shadow__Small */
  box-shadow: 0px 4px 8px 0px rgba(71, 83, 103, 0.1);
}

.content-container {
  position: absolute;
  display: flex;
  padding: 24px;
  flex-direction: column;
  align-items: flex-start;
  gap: 24px;
  border-radius: 8px;
  background: var(--White);
  bottom: 0;
  height: 132px;
  transform: scale(0.9);
  overflow: hidden;
  transition: all 0.3s;
}

.tag {
  display: flex;
  height: 28px;
  padding: 0px 8px;
  justify-content: center;
  align-items: center;
  gap: 6px;
  border-radius: 100px;
}

.card-wrapper:hover .content-container {
  height: 230px;
}
.cta {
  display: flex;
  justify-content: center;
  align-items: center;
  gap: 4px;
}
span.line {
  background: var(--grey-700);
}

.hamburger {
  width: max-content;
}

.hamburger .line {
  width: 7px;
  height: 2px;
  border-radius: 5px;
  background-color: var(--grey-700);
  display: block;
  transition-delay: 0.5s;
  -webkit-transition: all 0.3s ease-in-out;
  -o-transition: all 0.3s ease-in-out;
  transition: all 0.5s ease-in-out;
}
#hamburger-4 .line:nth-child(2) {
  opacity: 0;
  margin-left: 0%;
}

.card-wrapper:hover #hamburger-4 .line:nth-child(1),
.card-wrapper:hover #hamburger-4 .line:nth-child(3) {
  width: 7px;
}

.card-wrapper:hover #hamburger-4 .line:nth-child(2) {
  opacity: 1;
  margin-left: 100%;
}

#hamburger-4 .line:nth-child(1) {
  -webkit-transform: translateX(10px) rotate(45deg);
  -ms-transform: translateX(10px) rotate(45deg);
  -o-transform: translateX(10px) rotate(45deg);
  transform: translateX(10px) rotate(45deg);
}

#hamburger-4 .line:nth-child(3) {
  -webkit-transform: translateX(10px) rotate(-45deg);
  -ms-transform: translateX(10px) rotate(-45deg);
  -o-transform: translateX(10px) rotate(-45deg);
  transform: translateX(10px) rotate(-45deg);
}
.card-wrapper:hover .cta span {
  color: var(--grey-900);
}
.card-wrapper:hover .hamburger .line {
  background-color: var(--primary-primary-500-base);
}
</style>
