<template>
  <footer>
    <div class="footer-container">
      <div class="footer-wrapper" v-for="(wrapData, index) in FooterData" :key="index">
        <component
          :is="wrapData.category === 'company' ? Logo : 'h5'"
          class="text-heading-small-medium medium text-grey-900-base"
          >{{ wrapData.category }}</component
        >
        <div class="footer-group">
          <WebFooterLinks
            :link="data.link"
            :text="data.name"
            :type="data.type"
            v-for="(data, dataIndex) in wrapData.items"
            :key="dataIndex"
          />
        </div>
      </div>
    </div>
    <p class="copyright text-body-small-regular regular text-grey-700">
      All rights reserved. © 2023, IPC-Africa
    </p>
  </footer>
</template>

<script setup>
import { ref } from "vue";
import Logo from "../Logo.vue";

const FooterData = ref([
  {
    category: "company",
    items: [
      { name: "About Us", link: "/" },
      { name: "Help/FAQ", link: "/" },
      { name: "Blog", link: "/" },
      { name: "Careers", link: "/" },
    ],
  },
  {
    category: "Customers",
    items: [
      { name: "Restaurants", link: "/" },
      { name: "Hotels", link: "/" },
      { name: "Retail suppliers", link: "/" },
      { name: "Caterers", link: "/" },
      { name: "Food businesses", link: "/" },
    ],
  },
  {
    category: "Legal",
    items: [
      { name: "Legal Policy", link: "/" },
      { name: "Terms of Use", link: "/" },
    ],
  },
  {
    category: "Contact us",
    items: [
      { name: "admin@ipc-africa.com", type: "mail" },
      { name: "0906 182 7124", type: "number" },
      { name: "Twitter", link: "/" },
      { name: "Instagram", link: "/" },
      { name: "LinkedIn", link: "/" },
    ],
  },
]);
</script>

<style scoped>
footer {
  display: flex;
  max-width: 1440px;
  width: 100%;
  flex-direction: column;
  align-items: center;
  gap: 72px;
}
.footer-container {
  display: flex;
  gap: 24px;
  max-width: 80%;
  margin-inline: auto;
  width: 100%;
  justify-content: space-between;
}

.footer-wrapper {
  display: flex;
  flex-direction: column;
  align-items: flex-start;
  gap: 24px;
  width: 121px;
}

.footer-group {
  display: flex;
  flex-direction: column;
  align-items: flex-start;
  gap: 15px;
}

.copyright {
  text-align: center;
  margin-bottom: 96px;
}

@media screen and (max-width: 600px) {
  /* Media query for screens with a maximum width of 600px (adjust as needed) */
  .footer-container {
    flex-wrap: wrap;
  }
  .footer-wrapper:nth-child(1) {
    order: 1;
  }
  .footer-wrapper:nth-child(2) {
    order: 2;
  }
  .footer-wrapper:nth-child(3) {
    order: 4;
  }
  .footer-wrapper:nth-child(4) {
    order: 3;
  }
}
@media (max-width: 333px) {
  .footer-container {
    max-width: 100%;
    padding-inline: 16px;
    justify-content: center;
  }
  .footer-wrapper,
  .footer-group {
    width: 100%;
    align-items: center;
  }
}
</style>
