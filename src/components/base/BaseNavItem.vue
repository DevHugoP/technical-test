<template>
  <a href="#" class="nav-item" :class="{ active }">
    <img :src="require(`@/assets/icons/${icon}`)" :alt="label">
    <span>{{ label }}</span>
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

.nav-item img {
  width: 20px;
  height: 20px;
  margin-right: 0.5rem;
}

.nav-item.active {
  background-color: #4BD6B9;
  color: white;
}

.nav-item:hover:not(.active) {
  background-color: #f5f5f5;
}
</style>