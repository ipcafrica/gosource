<template>
    <div class="form-group">
      <input
        class="form-input"
        required="required"
        :class="{ 'input-error': inValid }"
        :type="type"
        :id="id"
        :name="id"
        :value="value"
        @input="$emit('updateValue', $event.target.value)"
      />
      <span>{{ label }}</span>
    </div>
    <div  v-if="ctaClicked" class="message-container">
      <WaitlistInputMessage :msg="msg" :msgType="msgType" />
    </div>
  </template>
    
    <script setup>
    import { ref, defineProps, defineEmits } from 'vue';
    
    const props = defineProps({
    label: {
        type: String,
        required: true,
      },
      msgType: {
        type: String,
        default: "",
      },
      msg: {
        type: String,
        default: "",
      },
      inValid: {
        type: Boolean,
        default: false,
      },
      value: {
        type: String,
        default: "",
      },
      ctaClicked: {
        type: Boolean,
        default: false,
      },
      type: {
        type: String,
        default: "text",
      },
      id: {
        type: String,
        default: "",
      },
    });
    
    const emits = defineEmits(['updateValue']);
    </script>
    
  <style scoped>
  .message-container {
  animation: fadeIn 0.3s ease-out;
}
@keyframes slideLeft {
  from {
    transform: translateX(100%);
  }

  to {
    transform: translateX(0);
  }
}
@keyframes fadeIn {
  from {
    opacity: 0;
    transform: translateY(-20px);
  }
  to {
    opacity: 1;
    transform: translateY(0);
  }
}
  .form-group {
    position: relative;
    margin-bottom: 5px;
  }
  
  input {
    max-width: 100%;
    width: 343px;
    border-radius: 12px;
    height: 56px;
    padding: 16px;
    border: 1px solid var(--grey-100);
    transition: 0.3s ease-in-out;
    color: var(--grey-900-base);
    outline: none;
    font-family: var(--primary---font--family);
    font-size: 14px;
    font-style: normal;
    font-weight: 400;
    line-height: 21px;
    letter-spacing: -0.2px;
  }
  span {
    position: absolute;
    left: 0;
    /* top: 8px; */
    padding: 16px;
    pointer-events: none;
    color: var(--grey-500);
    transition: 0.5s ease-in-out;
    font-family: var(--primary---font--family);
    font-size: 14px;
    font-style: normal;
    font-weight: 400;
    line-height: 21px;
    letter-spacing: -0.2px;
  }
  .form-group input:valid~span,
  .form-group input:focus~span {
    color: var(--grey-500);
    transform: translateX(10px) translateY(8px);
    font-size: 12px;
    font-style: normal;
    font-weight: 400;
    line-height: 18px;
    padding: 0 5px;
  }
  
  .form-group input:hover {
    border: 1px solid var(--primary-primary-500-base);
  }
  input:active,
  input:focus {
    border-radius: 12px;
    padding-top: 32px;
    border: 1px solid var(--primary-primary-500-base);
    background: var(--White);
    box-shadow: 0px 0px 0px 3px #e7f6ec;
  }
  input:required:valid {
  padding-top: 32px;
}
.input-error {
    border: 1px solid var(--negative-500-base);
  }

  @media screen and (max-width:675px) {
    .form-input {
        max-width: 100%;
      width: 100%;
      /* height: 100px; */
      border-radius: 12px;
      height: 56px;
      padding: 16px;
      font-size: 16px;
      border: 1px solid var(--grey-100);
      transition: border-color 0.3s ease, box-shadow 0.3s ease;
    }
    .input-error {
    border: 1px solid var(--negative-500-base);
  }
  }
  </style>
    