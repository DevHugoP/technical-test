<template>
  <a href="#" class="nav-item" :class="{ active }">
    <img :src="`src/assets/icons/${icon}`" :alt="label">
    <span class="nav-item-label">{{ label }}</span>
  </a>
</template>

<script>
export default {
  name: 'BaseNavItem',
  props: {
    icon: {
      type: String,
      required: true
    },
    label: {
      type: String,
      required: true
    },
    active: {
      type: Boolean,
      default: false
    }
  }

}
</script>

<style scoped>
.nav-item {
  display: flex;
  align-items: center;
  padding: 0.5rem 1rem;
  border-radius: 2rem;
  text-decoration: none;
  color: #666;
  font-weight: 500;
  transition: all 0.2s;
}

.nav-item .nav-item-label {
  color: #072635
}

.nav-item img {
  width: 20px;
  height: 20px;
  margin-right: 0.5rem;
}

.nav-item.active {
  background-color: #01F0D0;
  color: white;
}

.nav-item:hover:not(.active) {
  background-color: #f5f5f5;
}
</style>