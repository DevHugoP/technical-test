
// components/dashboard/PatientDashboard.vue
<template>
  <div class="patient-dashboard">
    <div class="dashboard-content">
      <h2 class="section-title">Diagnosis History</h2>
      
      <!-- Blood Pressure Chart Section -->
      <BloodPressureChart :chartData="patientData.bloodPressure" />
      
      <!-- Vital Signs Section -->
      <div class="vital-signs">
        <VitalSignCard 
          v-for="(sign, index) in patientData.vitalSigns" 
          :key="index" 
          :vitalSign="sign" 
        />
      </div>
      
      <!-- Diagnostic List Section -->
      <DiagnosticList :diagnoses="patientData.diagnoses" />
    </div>
    
    <PatientInfoSidebar 
      :patient="patientData"
      :labResults="patientData.labResults" 
    />
  </div>
</template>

<script>
import BloodPressureChart from './BloodPressureChart.vue'
import DiagnosticList from './DiagnosticList.vue'
import PatientInfoSidebar from './PatientInfoSidebar.vue'
import VitalSignCard from './VitalSignCard.vue'

export default {
  name: 'PatientDashboard',
  components: {
    BloodPressureChart,
    VitalSignCard,
    DiagnosticList,
    PatientInfoSidebar
  },
  props: {
    patientData: {
      type: Object,
      required: true
    }
  }
}
</script>

<style scoped>
.patient-dashboard {
  flex: 1;
  display: flex;
  overflow: hidden;
}

.dashboard-content {
  flex: 1;
  padding: 2rem;
  overflow-y: auto;
}

.section-title {
  font-size: 1.5rem;
  font-weight: 600;
  margin-bottom: 1.5rem;
  color: #333;
}

.vital-signs {
  display: grid;
  grid-template-columns: repeat(3, 1fr);
  gap: 1rem;
  margin-bottom: 2rem;
}
</style>
