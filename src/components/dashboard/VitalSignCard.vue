
// components/dashboard/VitalSignCard.vue
<template>
  <div class="vital-card" :class="{ 'status-low': isLowStatus }">
    <div class="vital-icon">
      <img :src="require(`@/assets/icons/${vitalSign.icon}`)" :alt="vitalSign.name">
    </div>
    <div class="vital-info">
      <h4>{{ vitalSign.name }}</h4>
      <div class="vital-value">{{ vitalSign.value }}</div>
      <div class="vital-status" :class="statusClass">
        <span v-if="isLowStatus">▼</span>
        {{ vitalSign.status }}
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: 'VitalSignCard',
  props: {
    vitalSign: {
      type: Object,
      required: true
    }
  },
  computed: {
    isLowStatus() {
      return this.vitalSign.status.includes('Lower');
    },
    statusClass() {
      if (this.vitalSign.status === 'Normal') return 'status-normal';
      if (this.vitalSign.status.includes('Lower')) return 'status-low';
      if (this.vitalSign.status.includes('Higher')) return 'status-high';
      return '';
    }
  }
}
</script>

<style scoped>
.vital-card {
  background-color: #e8f7ff;
  border-radius: 10px;
  padding: 1.5rem;
  display: flex;
  align-items: flex-start;
  gap: 1rem;
}

.vital-card.status-low {
  background-color: #fff0f0;
}

.vital-icon {
  width: 50px;
  height: 50px;
  border-radius: 50%;
  background-color: white;
  display: flex;
  align-items: center;
  justify-content: center;
}

.vital-icon img {
  width: 30px;
  height: 30px;
}

.vital-info h4 {
  font-size: 0.9rem;
  font-weight: 500;
  margin: 0 0 0.5rem 0;
}

.vital-value {
  font-size: 1.5rem;
  font-weight: 700;
  margin-bottom: 0.25rem;
}

.vital-status {
  font-size: 0.8rem;
  color: #666;
}

.status-normal {
  color: #27ae60;
}

.status-low {
  color: #3498db;
}

.status-high {
  color: #e74c3c;
}
</style>