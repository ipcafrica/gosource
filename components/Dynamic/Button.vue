<template>
  <button
    @click="emitFunction"
    class="btn"
    :class="buttonClasses"
    :style="buttonStyles"
    :disabled="disabled"
  >
    <div class="" v-if="showText">{{ buttonText }}</div>
    <slot name="svg"></slot>
  </button>
</template>
  
  <script>
export default {
  props: {
    buttonText: {
      type: String,
      required: true,
    },
    size: {
      type: String,
      required: true,
    },
    type: {
      type: String,
      required: true,
    },
    icon: {
      type: String,
    },
    showText: {
      type: Boolean,
      default: true,
    },
    disabled: {
      type: Boolean,
      default: false,
    },
  },
  computed: {
    buttonClasses() {
      return {
        // Button size
        small: this.size === "small",
        standard: this.size === "standard",
        large: this.size === "large",
        micro: this.size === "micro",
        // Button type
        primary: this.type === "primary",
        secondary: this.type === "secondary",
        ghost: this.type === "ghost",
        neutral: this.type === "neutral",
        // icon position
        "icon-left": this.icon === "icon-left",
        "icon-right": this.icon === "icon-right",
        "icon-button": this.showText === false,
      };
    },
    buttonStyles() {
      return {
        // Define your CSS styles based on size
      };
    },
  },
  methods: {
    emitFunction() {
      this.$emit("clickButton");
    },
  },
};
</script>

<style scoped>
button {
  border-radius: 100px;
  outline: 0px;
  margin: 0px;
  border: 0px;
}
button.large {
  height: 48px;
  padding: 0px 24px;
  justify-content: center;
  align-items: center;
  gap: 8px;
}

button.medium {
  height: 40px;
  padding: 0px 20px;
  justify-content: center;
  align-items: center;
  gap: 8px;
}

button.small {
  height: 32px;
  padding: 0px 16px;
  justify-content: center;
  align-items: center;
  gap: 4px;
}

button.micro {
  height: 24px;
  padding: 0px 12px;
  justify-content: center;
  align-items: center;
  gap: 4px;
}
button.primary {
  color: var(--white);
  background: var(--primary-500-base);
}
button.primary:hover {
  color: var(--white, #fff);
  background: var(--primary-600-base);
}
button.primary:focus,
button.primary:active {
  color: var(--white, #fff);
  background-color: var(--primary-700);
}
button.primary:disabled {
  background-color: var(--grey-300);
}
button.icon-right {
  flex-direction: row;
}
button.icon-left {
  flex-direction: row-reverse;
}
</style>