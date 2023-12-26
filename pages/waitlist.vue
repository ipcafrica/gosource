<template>
  <div class="container">
    <div class="sub-container">
      <div class="top">
        <div class="logo">
          <Logo />
        </div>
      </div>
      <div class="track">
        <div class="trackingBar">
          <WebTrackingBar :step="step" :inValid="inValided" v-if="!showModal" />
        </div>
      </div>
      <div
        class="modal-container"
        v-if="!showModal"
        :class="{ fadeIn: step > prevStep, 'slide-right': step < prevStep }"
      >
        <div class="flexed-modal">
          <div class="first-modal" v-if="step === 1">
            <div class="first-modal-text">
              <div class="first-modal-header">
                <h3 class="heading-3-medium">How do you want to use GoSource?</h3>
              </div>
              <div class="first-modal-snippet">
                <p class="body-large-regular">
                  We procure directly from farmers and manufacturers to get you the best
                  at unbeatable prices.
                </p>
              </div>
            </div>
            <div class="first-modal-card">
              <div class="modal-cards" v-for="(card, index) in cards" :key="index">
                <DynamicSelectCard
                  class="dynamic"
                  :card="card"
                  :selectedItem="selectedCard"
                  @selectItem="selectItem"
                />
              </div>
            </div>
            <div class="modal-button">
              <DynamicButton
                @clickButton="nextModal"
                class="primary-btn-large btn"
                buttonText="Continue"
                size="large"
                type="primary"
                :disabled="selectedCard == ''"
                :showText="true"
              />
            </div>
          </div>

          <div class="second-modal" v-if="step === 2">
            <div class="second-modal-text">
              <div class="second-modal-header">
                <h3 class="heading-3-medium">
                  Join the waitlist and we will give you access to Beta Testing
                </h3>
              </div>
            </div>
            <div class="second-modal-input">
              <div class="first-input">
                <DynamicTextInput
                  :label="label1"
                  :type="text"
                  :id="businessName"
                  :value="businessName"
                  :inValid="ctaClicked && !businessName ? true : false"
                  :msg="ctaClicked && !businessName ? 'Business Name is required' : ''"
                  msgType="error"
                  @update-value="updateValue($event, 'business-name')"
                  :ctaClicked="ctaClicked"
                />
              </div>
              <div class="second-input">
                <DynamicTextInput
                  :label="label3"
                  :type="email"
                  :id="email"
                  :value="email"
                  :inValid="ctaClicked && !isEmailValid ? true : false"
                  :msg="ctaClicked && !isEmailValid ? 'Email is not valid' : ''"
                  :msgType="isEmailValid ? 'success' : 'error'"
                  @update-value="updateValue($event, 'email')"
                  :ctaClicked="ctaClicked"
                />
              </div>
            </div>
            <div class="second-modal-button">
              <DynamicButton
                @clickButton="addToWaitlist('business')"
                class="primary-btn-large btn"
                :class="{ bton: isLoading }"
                buttonText="Join waitlist"
                size="large"
                type="primary"
                :disabled="disabled"
                :isLoading="isLoading"
                :showText="true"
              />
            </div>
          </div>

          <div class="third-modal" v-if="step === 3">
            <div class="third-modal-text">
              <div class="third-modal-header">
                <h3 class="heading-3-medium">
                  Join the waitlist and we will give you access to Beta Testing
                </h3>
              </div>
            </div>
            <div class="third-modal-input">
              <div class="first-input">
                <DynamicTextInput
                  :label="label2"
                  :type="text"
                  :id="fullName"
                  :value="fullName"
                  :inValid="ctaClicked && !fullName ? true : false"
                  :msg="ctaClicked && !fullName ? 'Full Name is required' : ''"
                  msgType="error"
                  @update-value="updateValue($event, 'full-name')"
                  :ctaClicked="ctaClicked"
                />
              </div>
              <div class="second-input">
                <DynamicTextInput
                  :label="label3"
                  :type="email"
                  :id="email"
                  :value="email"
                  :inValid="ctaClicked && !isEmailValid ? true : false"
                  :msg="ctaClicked && !isEmailValid ? 'Email is not valid' : ''"
                  :msgType="isEmailValid ? 'success' : 'error'"
                  @update-value="updateValue($event, 'email')"
                  :ctaClicked="ctaClicked"
                />
              </div>
            </div>
            <div class="third-modal-button">
              <DynamicButton
                @clickButton="addToWaitlist('individual')"
                class="primary-btn-large btn"
                :class="{ bton: isLoading }"
                buttonText="Join waitlist"
                size="large"
                type="primary"
                :disabled="disabled"
                :isLoading="isLoading"
                :showText="true"
              />
            </div>
          </div>
        </div>
      </div>
      <div class="congratulations" v-if="showModal" :class="{ fadeIn: showModal }">
        <div class="final-modal">
          <div class="final-image">
            <svg
              xmlns="http://www.w3.org/2000/svg"
              width="129"
              height="128"
              viewBox="0 0 129 128"
              fill="none"
            >
              <g clip-path="url(#clip0_999_19223)">
                <rect x="0.5" width="128" height="128" rx="64" fill="#E8F8E9" />
                <path
                  d="M115.051 16.4891C113.615 16.9396 111.744 17.4663 109.257 18.0658C109.32 13.075 110.37 12.0103 111.63 12.58C111.63 12.58 111.641 12.5852 111.642 12.5909C112.802 13.1138 114.143 15.0051 115.051 16.4891Z"
                  fill="#D4F2D6"
                />
                <path
                  d="M111.628 12.5785C110.368 12.0087 109.318 13.0734 109.255 18.0642C109.239 19.4869 109.305 21.2357 109.468 23.3613C108.015 23.9491 105.523 24.8332 100.779 25.9765C100.329 22.7546 100.309 20.1165 100.516 17.9858C100.722 15.8552 102.232 13.9965 104.321 13.3749C109.356 11.8774 111.083 12.0908 111.628 12.5785Z"
                  fill="#65CF6A"
                />
                <path
                  d="M51.7142 118.815C49.3866 119.545 46.3546 120.399 42.323 121.371C42.4249 113.281 44.1275 111.555 46.169 112.479C46.169 112.479 46.1878 112.487 46.1882 112.497C48.0696 113.344 50.243 116.41 51.7142 118.815Z"
                  fill="#D4F2D6"
                />
                <path
                  d="M46.1656 112.477C44.1242 111.553 42.4215 113.279 42.3197 121.368C42.293 123.674 42.4004 126.509 42.6639 129.954C40.3093 130.907 36.2705 132.34 28.5813 134.193C27.8517 128.971 27.8186 124.695 28.1539 121.241C28.4892 117.788 30.9368 114.775 34.3214 113.768C42.483 111.34 45.2824 111.686 46.1656 112.477Z"
                  fill="#95DE98"
                />
                <path
                  d="M121.679 81.656L119.563 86.9559C117.545 85.2746 115.85 83.6898 114.431 82.2031C112.467 80.145 111.198 77.402 111.563 74.5806C111.687 73.5529 111.921 72.5384 112.308 71.5693C112.577 72.0021 112.877 72.4549 113.206 72.9117C115.025 75.4588 117.737 78.37 121.679 81.656Z"
                  fill="#D4F2D6"
                />
                <path
                  d="M148.385 61.9791C145.753 65.5623 139.806 68.8912 126.858 69.1075C120.204 69.2178 115.888 70.6948 113.199 72.9069C112.87 72.4501 112.57 71.9973 112.302 71.5646C114.041 67.1682 118.72 63.6584 129.101 63.4867C138.377 63.3305 143.85 61.6335 147 59.4117C148.704 58.2091 149.731 56.86 150.315 55.5126C150.398 57.2658 150.078 59.6794 148.385 61.9791Z"
                  fill="#65CF6A"
                />
                <path
                  d="M95.2216 60.1906C95.49 85.5575 79.3393 100.959 71.2304 105.489C60.2135 100.903 36.8039 86.799 31.301 67.0692C24.4224 42.407 43.2127 23.6167 56.6344 21.6034C70.056 19.5902 94.886 28.482 95.2216 60.1906Z"
                  fill="#19B820"
                />
                <path
                  d="M71.4395 105.386C73.3409 108.91 79.224 117.499 87.5454 123.673C95.8668 129.847 103.204 130.496 105.832 130.049"
                  stroke="#98A2B3"
                  stroke-width="2.66667"
                />
                <path
                  d="M57.2171 37.8915C43.6764 45.1315 42.1337 66.7676 43.055 76.6807C30.2671 63.2766 37.5625 38.7692 46.3958 31.8972C59.6011 21.6238 74.1429 28.8415 57.2171 37.8915Z"
                  fill="#65CF6A"
                />
                <path
                  d="M73.957 105.89L72.1115 104.715L70.6016 105.051V107.735C72.0779 107.735 73.4537 106.505 73.957 105.89Z"
                  fill="#19B820"
                />
                <path
                  d="M88.7151 -2.92388C87.3875 0.138513 85.0656 3.1895 81.2112 5.90915C76.676 -1.12325 70.5739 -6.02995 65.3493 -9.27207L70.5503 -22.3013C76.7152 -18.4735 84.1268 -12.3256 88.7149 -3.09917C88.7149 -3.09917 88.7109 -3.08909 88.7029 -3.06894C88.7029 -3.06894 88.6969 -2.96618 88.6999 -2.92992L88.7151 -2.92388Z"
                  fill="#95DE98"
                />
                <path
                  d="M23.9356 56.2077L19.1509 68.194C12.9468 63.024 8.08789 58.2578 4.32001 53.9036C2.1623 51.4102 0.82284 48.2802 0.788097 44.9829C0.771278 43.3867 0.853636 41.7887 1.05857 40.2064C1.33799 37.8821 1.86828 35.5879 2.74316 33.3962C3.35131 34.375 4.029 35.399 4.77319 36.4321C8.88739 42.1925 15.021 48.7764 23.9356 56.2077Z"
                  fill="#B8E9BA"
                />
                <path
                  d="M84.3327 11.7074C78.3817 19.811 64.9323 27.3396 35.6479 27.8287C20.6007 28.078 10.8385 31.4184 4.75839 36.4213C4.01421 35.3883 3.33651 34.3642 2.72837 33.3855C6.66226 23.4428 17.2433 15.5052 40.7222 15.1169C61.6988 14.7636 74.0779 10.9258 81.2006 5.90097C85.055 3.18132 87.3769 0.130335 88.6984 -2.91694C88.8856 1.04801 88.1611 6.50654 84.3327 11.7074Z"
                  fill="#95DE98"
                />
              </g>
              <defs>
                <clipPath id="clip0_999_19223">
                  <rect x="0.5" width="128" height="128" rx="64" fill="white" />
                </clipPath>
              </defs>
            </svg>
          </div>
          <div class="final-text">
            <div class="final-header">
              <h3 class="heading-3-medium">
                You’ve been successfully added to the waitlist!
              </h3>
            </div>
            <div class="final-snippet">
              <p class="body-large-regular">
                We will let you know when you’ve been given access to join the Private
                Beta testing.
              </p>
            </div>
          </div>
          <div class="final-button">
            <DynamicButton
              @clickButton="nextModal"
              class="primary-btn-large btn"
              buttonText="Go to website"
              size="large"
              type="primary"
              :disabled="false"
              :showText="true"
            />
          </div>
        </div>
      </div>
    </div>
    <WebFooter />
  </div>
</template>

<script>
import axios from "axios";
export default {
  data() {
    return {
      step: 1,
      prevStep: 1,
      showModal: false,
      label1: "Business name",
      label2: "Full name",
      label3: "Email address",
      cards: [
        {
          svg: "/business.svg",
          title: "GoSource for Business",
          value: "business",
          snippet:
            "Get access to buy on credit, instant invoice, fast payments & 24hours delivery",
        },
        {
          svg: "/individual.svg",
          value: "individual",
          title: "GoSource for Individual",
          snippet:
            "Buy your food items with discounts, lesser prices and get them in 24hours",
        },
      ],
      selectedCard: "",
      text: "",
      fullName: "",
      businessName: "",
      email: "",
      ctaClicked: false,
      inValided: true,
      customerType: "INDIVIDUAL",
      disabled: false,
      isLoading: false,
    };
  },
  methods: {
    updateValue(e, name) {
      if (name === "business-name") {
        this.businessName = e;
      } else if (name === "email") {
        this.email = e;
      } else if (name === "full-name") {
        this.fullName = e;
      }
    },
    selectItem(value) {
      this.selectedCard = value;
    },
    nextModal() {
      console.log("working");
      if (this.selectedCard === "business") {
        this.prevStep = this.step;
        this.step = 2;
      } else if (this.selectedCard === "individual") {
        this.prevStep = this.step;
        this.step = 3;
      } else {
        this.slideDirection = "slide-left";
      }
    },
    addToWaitlist(type) {
      this.ctaClicked = true;
      if (type === "individual") {
        if (!this.fullName || !this.isEmailValid) {
          return;
        }
      } else {
        if (!this.businessName || !this.isEmailValid) {
          return;
        }
      }
      this.inValided = false;
      this.isLoading = true;
      this.addToWaitlistCall(type);
    },

    async addToWaitlistCall(type) {
      let data;

      if (type === "individual") {
        data = {
          fullName: this.fullName,
          email: this.email,
          customerType: this.customerType,
        };
      } else {
        data = {
          businessName: this.businessName,
          email: this.email,
        };
      }
      console.log(data);
      try {
        const response = await axios.post(
          "https://api.ipc-africa.com/api/v1/waitlist",
          data
        );
        console.log(response);

        this.showModal = true;
      } catch (error) {
        console.error("An error occurred during the request:", error.response);
      }
      // finally {

      // }
    },
  },
  computed: {
    isEmailValid() {
      // Define a regular expression for email validation
      const emailRegex = /^(([^<>()[\]\\.,;:\s@"]+(\.[^<>()[\]\\.,;:\s@"]+)*)|(".+"))@((\[[0-9]{1,3}\.[0-9]{1,3}\.[0-9]{1,3}\.[0-9]{1,3}\])|(([a-zA-Z\-0-9]+\.)+[a-zA-Z]{2,}))$/;
      // Check if the input email matches the regular expression
      return emailRegex.test(this.email);
    },
  },
};
</script>

<style scoped>
.fadeIn {
  animation: fadeIn 1s ease-in-out;
}

@keyframes fadeIn {
  from {
    opacity: 0;
  }

  to {
    opacity: 1;
  }
}

.slide-left {
  animation: slideLeft 0.4s ease-in-out;
}

.slide-right {
  animation: slideRight 0.4s ease-in-out;
}

@keyframes slideLeft {
  from {
    transform: translateX(100%);
  }

  to {
    transform: translateX(0);
  }
}

@keyframes slideRight {
  from {
    transform: translateX(-100%);
  }

  to {
    transform: translateX(0);
  }
}

@keyframes slideTop {
  from {
    transform: translateY(-100%);
    opacity: 0;
  }

  to {
    transform: translateY(0);
    opacity: 1;
  }
}

.slide-top {
  animation: slideTop 0.5s ease-in-out;
}

.container {
  background-color: var(--white);
}

.sub-container {
  background-color: var(--white);
}

.top {
  position: fixed;
  top: 0;
  left: 0;
  width: 100%;
  background-color: #fff;
  height: 80px;
  z-index: 1000;
  padding-left: 100px;
  display: flex;
  align-items: center;
}

.track {
  margin: 150px 0px 0px 310px;
}

.modal-container {
  margin: 24px 0px 0px 310px;
  display: flex;
  flex-direction: column;
}

.first-modal {
  margin-top: 24px;
  display: flex;
  flex-direction: column;
  gap: 48px;
}

.first-modal-header,
.first-modal-text,
.second-modal-header,
.third-modal-header {
  width: 400px;
}

.first-modal-snippet {
  margin-top: 8px;
}

.first-modal-snippet p {
  color: var(--grey-500);
}

.first-modal-card {
  display: flex;
  gap: 24px;
}

.second-modal,
.third-modal {
  margin-top: 24px;
  display: flex;
  flex-direction: column;
  gap: 48px;
}

.first-input {
  margin-bottom: 24px;
}

.congratulations {
  margin: auto;
  display: flex;
  align-items: center;
  justify-content: center;
}

.final-modal {
  width: 330px;
  display: flex;
  flex-direction: column;
  justify-content: center;
  align-items: center;
  gap: 39px;
}

.final-text {
  display: flex;
  flex-direction: column;
  gap: 8px;
}

.final-header h3 {
  text-align: center;
}

.final-snippet p {
  text-align: center;
  color: var(--grey-500);
}

.sub-container {
  background: var(--white);
  width: 100%;
  padding-bottom: 100px;
}

.bton {
  width: 151px;
}

@media screen and (max-width: 600px) {
  .track {
    margin: 124px 0px 0px 0px;
    display: flex;
    justify-content: center;
    align-items: center;
  }

  .container {
    background: var(--white);
    width: 100%;
  }

  .sub-container {
    background: var(--white);
    width: 100%;
    padding-bottom: 100px;
  }

  .top {
    position: fixed;
    top: 0;
    left: 0;
    width: 100%;
    background-color: #fff;
    height: 80px;
    padding: 0px;
    /* border: 1px solid red; */
    display: flex;
    justify-content: center;
    align-items: center;
  }

  .modal-container {
    margin: 24px 0px 0px 0px;
    /* border: 1px solid blue; */
  }

  .flexed-modal {
    padding: 0px 24px;
  }

  .first-modal-header,
  .first-modal-text,
  .second-modal-header,
  .third-modal-header {
    width: 100%;
  }

  .first-modal-header h3,
  .second-modal-header h3,
  .third-modal-header h3 {
    color: var(--grey-900-base);
    font-family: var(--graphikMedium);
    font-size: 20px;
    font-style: normal;
    font-weight: 500;
    line-height: 30px;
    letter-spacing: -0.3px;
  }

  .first-modal-snippet p {
    color: var(--grey-500);
    font-family: var(--InterRegular);
    font-size: 14px;
    font-style: normal;
    font-weight: 400;
    line-height: 21px;
    letter-spacing: -0.2px;
  }

  .first-modal-card {
    display: flex;
    flex-direction: column;
    gap: 24px;
  }

  .trackingBar {
    display: flex;
    justify-content: center;
    align-items: center;
  }

  .btn {
    width: 100%;
  }

  .congratulations {
    padding: 0px 24px;
    display: flex;
    align-items: center;
    justify-content: center;
    margin-top: 24px;
  }

  .final-modal {
    width: 100%;
    display: flex;
    flex-direction: column;
    justify-content: center;
    align-items: center;
    gap: 39px;
  }

  .final-header h3 {
    color: var(--grey-900-base);
    font-family: var(--graphikMedium);
    font-size: 20px;
    font-style: normal;
    font-weight: 500;
    line-height: 30px;
    letter-spacing: -0.3px;
  }

  .final-snippet p {
    font-family: var(--InterRegular);
    font-size: 14px;
    font-style: normal;
    font-weight: 400;
    line-height: 21px;
    letter-spacing: -0.2px;
  }
}
</style>
