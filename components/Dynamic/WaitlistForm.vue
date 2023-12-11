<!-- DynamicModal.vue -->
<template>
    <div class="dynamic-modal">
      <div class="modal-text">
        <div class="modal-header">
          <h3 class="heading-3-medium">{{ modalTitle }}</h3>
        </div>
      </div>
      <div class="modal-input">
        <div class="first-input">
          <DynamicTextInput
            :label="label1"
            :type="text"
            :id="input1Id"
            :value="input1Value"
            :inValid="ctaClicked && !input1Value ? true : false"
            :msg="ctaClicked && !input1Value ? input1ErrorMsg : ''"
            msgType="error"
            @update-value="updateValue($event, input1Name)"
            :ctaClicked="ctaClicked"
          />
        </div>
        <div class="second-input">
          <DynamicTextInput
            :label="label2"
            :type="email"
            :id="input2Id"
            :value="input2Value"
            :inValid="ctaClicked && !isEmailValid ? true : false"
            :msg="ctaClicked && !isEmailValid ? emailErrorMsg : ''"
            :msgType="isEmailValid ? 'success' : 'error'"
            @update-value="updateValue($event, input2Name)"
            :ctaClicked="ctaClicked"
          />
        </div>
      </div>
      <div class="modal-button">
        <DynamicButton
          @clickButton="$emit('addToWaitlist')"
          class="primary-btn-large btn"
          :class="{ bton: isLoading }"
          :buttonText="buttonText"
          size="large"
          type="primary"
          :disabled="disabled"
          :isLoading="isLoading"
          :showText="true"
        />
      </div>
    </div>
  </template>
  
  <script>
  import { ref, computed } from 'vue';
  import DynamicTextInput from '@/components/DynamicTextInput.vue';
  import DynamicButton from '@/components/DynamicButton.vue';
  
  export default {
    props: {
      modalTitle: String,
      label1: String,
      label2: String,
      input1Id: String,
      input2Id: String,
      input1Value: String,
      input2Value: String,
      input1Name: String,
      input2Name: String,
      ctaClicked: Boolean,
      isEmailValid: Boolean,
      input1ErrorMsg: String,
      emailErrorMsg: String,
      addToWaitlist: Function,
      buttonText: String,
      disabled: Boolean,
      isLoading: Boolean,
      text: String,
    },
    
    components: {
      DynamicTextInput,
      DynamicButton,
    },
    setup(props) {
      return {
        input1Value: ref(props.input1Value),
        input2Value: ref(props.input2Value),
        ctaClicked: ref(props.ctaClicked),
        isEmailValid: computed(() => props.isEmailValid),
        updateValue: (value, name) => props.updateValue(value, name),
      };
    },
  };
  </script>
  
  
  <script setup>
  import { ref, defineProps, defineEmits } from 'vue';
  
  const props = defineProps({
    modalTitle: {
      type: String,
      required: true,
    },
    label1: {
      type: String,
      default: "",
    },
    label12: {
      type: String,
      default: "",
    },
    input1Id:{
      type: String,
      default: "",
    },
    input2Id:{
      type: String,
      default: "",
    },
    input1Value:{
      type: String,
      default: "",
    },
    input2Value:{
      type: String,
      default: "",
    },
    input1Name:{
      type: String,
      default: "",
    },
    input2Name:{
      type: String,
      default: "",
    },
    isEmailValid: {
      type: Boolean,
      default: false,
    },
    ctaClicked: {
      type: Boolean,
      default: false,
    },
    input1ErrorMsg: {
      type: String,
      default: "text",
    },
    emailErrorMsg: {
      type: String,
      default: "text",
    },
    buttonText: {
      type: String,
      default: "text",
    },
    text: {
      type: String,
      default: "",
    },
    disabled:{
      type: Boolean,
      default: false,
    },
      isLoading: {
      type: Boolean,
      default: false,
    },
  });
  
  const emits = defineEmits(['updateValue']);
  </script>

  <style scoped>
  /* Add your styles here */
  </style>
  