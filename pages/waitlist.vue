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
          <TrackingBar :step="step" :inValid="inValided" v-if="!showModal" />
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
                <h3 class="medium text-heading-3-medium">How do you want to use GoSource?</h3>
              </div>
              <div class="first-modal-snippet">
                <p class="regular text-body-large-regular text-grey-500">
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
              <DynamicButtonMain
                @clickButton="nextModal"
                class="bold text-button-large w-auto btn"
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
                <h3 class="medium text-heading-3-medium">
                  Join the waitlist and we will give you access to Beta Testing
                </h3>
              </div>
            </div>
            <div class="second-modal-input">
              <div class="first-input">
                <WaitlistText-Input
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
                <WaitlistText-Input
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
              <DynamicButtonMain
                @clickButton="addToWaitlist('business')"
                class="bold text-button-large w-auto btn"
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
                <h3 class="medium text-heading-3-medium">
                  Join the waitlist and we will give you access to Beta Testing
                </h3>
              </div>
            </div>
            <div class="third-modal-input">
              <div class="first-input">
                <WaitlistText-Input
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
                <WaitlistText-Input
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
              <DynamicButtonMain
                @clickButton="addToWaitlist('individual')"
                class="bold text-button-large w-auto btn"
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
        <WaitlistSuccess-page @cliclickButton="nextModal"/>
      </div>
    </div>
   
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
.tried{
  border: 1px solid red;
}
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
  margin: 150px 0px 0px 21%;
  
}

.modal-container {
  margin: 24px 0px 0px 21%;
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

@media screen and (max-width: 675px) {

  .track {
    margin: 88px 0px 0px 0px;
    display: flex;
    justify-content: center;
    align-items: center;
    /* border: 1px solid red; */
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
    font-size: 20px;
    font-style: normal;
    font-weight: 500;
    line-height: 30px;
    letter-spacing: -0.3px;
  }

  .first-modal-snippet p {
    color: var(--grey-500);
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
