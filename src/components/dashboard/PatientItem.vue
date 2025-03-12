<template>
  <li class="patient-item" :class="{ active }">
    <div class="patient-info">
      <img :src="`/src/assets/patients/${patient.avatar}`" :alt="patient.name" />
      <div>
        <p class="patient-name">{{ patient.name }}</p>
        <p class="patient-details">{{ patient.gender }}, {{ patient.age }}</p>
      </div>
    </div>
  </li>
</template>

<script>
import BaseIconButton from '../base/BaseIconButton.vue';

export default {
  name: 'PatientItem',
  components: {
    BaseIconButton
  },
  props: {
    patient: {
      type: Object,
      required: true
    },
    active: {
      type: Boolean,
      default: false
    }
  },
};
</script>
<style scoped>
.patient-item {
  display: flex;
  align-items: center;
  justify-content: space-between;
  padding: 0.75rem 1.5rem;
  border-bottom: 1px solid #eee;
  cursor: pointer;
  transition: background-color 0.2s;
}

.patient-item.active {
  background-color: #e6f9f5;
}

.patient-item:hover:not(.active) {
  background-color: #f5f5f5;
}

.patient-info {
  display: flex;
  align-items: center;
  gap: 0.75rem;
}

.patient-info img {
  width: 40px;
  height: 40px;
  border-radius: 50%;
  object-fit: cover;
}

.patient-name {
  font-weight: 500;
  margin: 0;
}

.patient-details {
  font-size: 0.8rem;
  color: #666;
  margin: 0;
}
</style>
