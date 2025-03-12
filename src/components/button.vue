<template>
    <button :style="{ backgroundColor: color }" class="custom-button">
        <i v-if="icon" :class="icon"></i>
        {{ text }}
    </button>
</template>

<script>
export default {
    name: 'CustomButton',
    props: {
        text: {
            type: String,
            required: true
        },
        color: {
            type: String,
            default: '#000'
        },
        icon: {
            type: String,
            default: ''
        }
    }
}
</script>

<style scoped>
.custom-button {
    border: none;
    padding: 10px 20px;
    color: #fff;
    cursor: pointer;
    display: flex;
    align-items: center;
}

.custom-button i {
    margin-right: 8px;
}
</style>