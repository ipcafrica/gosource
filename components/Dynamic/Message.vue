<template>
    <div :class="['message', msgType]">
        <p class="body-micro-regular"> {{ msg }} </p>
    </div>
</template>

<script>
export default {
    props: {
        msg: {
            type: String,
            default: () => ''
        },
        msgType: {
            type: String,
            default: () => ''
        }
    }
}
</script>
<style scoped>

.message.error p {
    color: var(--negative-500-base);
}

.message.success p{
    color: var(--success-500);
}

</style>