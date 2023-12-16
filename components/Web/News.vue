<template>
  <div class="new-wrapper">
    <div class="new-tag">
      <img src="/images/Confetti.png" alt="" style="width: 12px" />
      <span class="base-font text-button-micro text-white">New</span>
    </div>
    <p class="body-large-regular regular text-white">
      9 popular markets in Lagos you need to visit if you need to buy pocket-friendly
      foodstuffs
    </p>
    <div class="">
      <svg
        xmlns="http://www.w3.org/2000/svg"
        width="16"
        height="16"
        viewBox="0 0 16 16"
        fill="none"
      >
        <path
          d="M9.62 3.95312L13.6667 7.99979L9.62 12.0465"
          stroke="white"
          stroke-width="2"
          stroke-miterlimit="10"
          stroke-linecap="round"
          stroke-linejoin="round"
        />
        <path
          d="M2.33331 8H13.5533"
          stroke="white"
          stroke-width="2"
          stroke-miterlimit="10"
          stroke-linecap="round"
          stroke-linejoin="round"
        />
      </svg>
    </div>
  </div>
</template>

<script setup></script>

<style scoped>
.new-wrapper {
  cursor: pointer;
  display: flex;
  height: 48px;
  padding: 19px 32px;
  justify-content: center;
  align-items: center;
  gap: 16px;
  background: var(--orange-orange-800);
  transition: all var(--animation-duration) ease-in-out;
}
.new-wrapper:hover {
  gap: 26px;
}
.new-tag {
  width: fit-content;
  display: flex;
  height: 24px;
  padding: 0px 12px;
  justify-content: center;
  align-items: center;
  gap: 4px;
  border-radius: 100px;
  background: var(--orange-orange-500);
}
svg {
  width: fixed;
}

@media (max-width: 960px) {
  .new-wrapper {
    height: 40px;
    padding: 8px 24px;
  }
  p {
    max-width: 60%;
    white-space: nowrap;
    overflow: hidden;
    text-overflow: ellipsis;
    font-size: 12px;
    line-height: 18px; /* 150% */
  }

  .new-tag {
    height: 16px;
    padding: 0px 8px;
    gap: 3.333px;
  }

  .new-tag span {
    font-size: 10px;
    line-height: 10px; /* 100% */
  }
}
</style>
