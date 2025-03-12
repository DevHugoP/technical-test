
<template>
  <button class="icon-button" @click="$emit('click')">
    <img :src="`@/assets/icons/${icon}`" :alt="altText || 'Icon'">
  </button>
</template>

<script>
export default {
  name: 'BaseIconButton',
  props: {
    icon: {
      type: String,
      required: true
    },
    altText: {
      type: String,
      default: ''
    }
  },
  emits: ['click']
}
</script>

<style scoped>
.icon-button {
  display: flex;
  align-items: center;
  justify-content: center;
  width: 35px;
  height: 35px;
  border-radius: 50%;
  border: none;
  background-color: transparent;
  cursor: pointer;
  transition: background-color 0.2s;
}

.icon-button img {
  width: 20px;
  height: 20px;
}

.icon-button:hover {
  background-color: #f5f5f5;
}
</style>