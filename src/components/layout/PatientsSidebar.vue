// components/layout/PatientsSidebar.vue
<template>
  <aside class="patients-sidebar">
    <div class="sidebar-header">
      <h2>Patients</h2>
      <div class="search-box">
        <img src="@/assets/icons/search.svg" alt="Search">
      </div>
    </div>
    
    <ul class="patients-list"  v-if="patients.length" >
      <PatientItem 
        v-for="patient in patients" 
        :key="patient.id"
        :patient="patient"
      />
    </ul>
  </aside>
</template>

<script>
import PatientItem from '../dashboard/PatientItem.vue';

export default {
  name: 'PatientsSidebar',
  components: {
    PatientItem
  },
  props: {
    patients: {
      type: Array,
      required: true
    },
    activePatient: {
      type: Number,
      required: true
    }
  },
  mounted() {
    console.log('Patients reçus dans PatientsSidebar:', this.patients);
  },
  emits: ['select-patient']
}
</script>

<style scoped>
.patients-sidebar {
  width: 300px;
  background-color: #f9f9f9;
  border-right: 1px solid #eee;
  overflow-y: auto;
}

.sidebar-header {
  display: flex;
  justify-content: space-between;
  align-items: center;
  padding: 1.5rem;
  border-bottom: 1px solid #eee;
}

.sidebar-header h2 {
  font-size: 1.25rem;
  font-weight: 600;
  color: #333;
}

.search-box {
  width: 35px;
  height: 35px;
  border-radius: 50%;
  background-color: #f2f2f2;
  display: flex;
  align-items: center;
  justify-content: center;
  cursor: pointer;
}

.search-box img {
  width: 18px;
  height: 18px;
}

.patients-list {
  list-style: none;
  padding: 0;
  margin: 0;
}
</style>