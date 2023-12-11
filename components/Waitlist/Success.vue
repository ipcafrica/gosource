<template>
     <div class="final-modal">
          <div class="final-image">
           <SvgSuccess-waitlist/>
          </div>
          <div class="final-text">
            <div class="final-header">
              <h3 class="text-heading-3-medium medium text-grey-900-base">
                You’ve been successfully added to the waitlist!
              </h3>
            </div>
            <div class="final-snippet">
              <p class="text-body-large-regular regular text-grey-500">
                We will let you know when you’ve been given access to join the Private
                Beta testing.
              </p>
            </div>
          </div>
          <div class="final-button">
            <DynamicButton
              @clickButton="$emit('clickButton')"
              class="bold text-button-large w-auto btn"
              buttonText="Go to website"
              size="large"
              type="primary"
              :disabled="false"
              :showText="true"
            />
          </div>
        </div>
</template>

<script setup>

</script>

<style scoped>
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
}
@media screen and (max-width: 750px) {
    .final-modal {
    width: 100%;
    display: flex;
    flex-direction: column;
    justify-content: center;
    align-items: center;
    gap: 39px;
  }
}
</style>