<template>
  <div class="app-container">
    <TechCareHeader />
    <div class="main-container">
      <PatientsSidebar :patients="patients" :activePatient="activePatient" @select-patient="selectPatient" />
      <PatientDashboard :patientData="patientData" />
    </div>
  </div>
</template>

<script>
import PatientDashboard from './components/dashboard/PatientDashboard.vue'
import PatientsSidebar from './components/layout/PatientsSidebar.vue'
import TechCareHeader from './components/layout/TechCareHeader.vue'

export default {
  name: 'App',
  components: {
    TechCareHeader,
    PatientsSidebar,
    PatientDashboard
  },
  data() {
    return {
      activePatient: 3, // Index du patient actif (Jessica Taylor)
      patients: [
        { id: 1, name: 'Emily Williams', gender: 'Female', age: 18, avatar: 'emily.png' },
        { id: 2, name: 'Ryan Johnson', gender: 'Male', age: 45, avatar: 'ryan.png' },
        { id: 3, name: 'Brandon Mitchell', gender: 'Male', age: 36, avatar: 'brandon.png' },
        { id: 4, name: 'Jessica Taylor', gender: 'Female', age: 28, avatar: 'jessica.png' },
        { id: 5, name: 'Samantha Johnson', gender: 'Female', age: 56, avatar: 'samantha.png' },
        { id: 6, name: 'Ashley Martinez', gender: 'Female', age: 54, avatar: 'ashley.png' },
        { id: 7, name: 'Olivia Brown', gender: 'Female', age: 32, avatar: 'olivia.png' },
        { id: 8, name: 'Tyler Davis', gender: 'Male', age: 19, avatar: 'tyler.png' },
        { id: 9, name: 'Kevin Anderson', gender: 'Male', age: 30, avatar: 'kevin.png' },
        { id: 10, name: 'Dylan Thompson', gender: 'Male', age: 36, avatar: 'dylan.png' },
        { id: 11, name: 'Nathan Evans', gender: 'Male', age: 58, avatar: 'nathan.png' },
        { id: 12, name: 'Mike Nolan', gender: 'Male', age: 31, avatar: 'mike.png' }
      ],
      patientData: {
        // Données du patient actif (Jessica Taylor)
        id: 4,
        name: 'Jessica Taylor',
        gender: 'Female',
        dateOfBirth: 'August 23, 1996',
        contact: '(415) 555-1234',
        emergency: '(415) 555-5678',
        insurance: 'Sunrise Health Assurance',
        bloodPressure: {
          systolic: 160,
          diastolic: 78,
          history: [
            { month: 'Oct. 2023', systolic: 120, diastolic: 110 },
            { month: 'Nov. 2023', systolic: 115, diastolic: 65 },
            { month: 'Dec. 2023', systolic: 160, diastolic: 110 },
            { month: 'Jan. 2024', systolic: 110, diastolic: 90 },
            { month: 'Feb. 2024', systolic: 150, diastolic: 75 },
            { month: 'Mar. 2024', systolic: 160, diastolic: 80 }
          ]
        },
        vitalSigns: [
          { name: 'Respiratory Rate', value: '20 bpm', status: 'Normal', icon: 'respiratory.svg' },
          { name: 'Temperature', value: '98.6°F', status: 'Normal', icon: 'temperature.svg' },
          { name: 'Heart Rate', value: '78 bpm', status: 'Lower than Average', icon: 'heartBPM.svg' }
        ],
        diagnoses: [
          { problem: 'Hypertension', description: 'Chronic high blood pressure', status: 'Under Observation' },
          { problem: 'Type 2 Diabetes', description: 'Insulin resistance and elevated blood sugar', status: 'Cured' },
          { problem: 'Asthma', description: 'Recurrent episodes of bronchial constriction', status: 'Inactive' }
        ],
        labResults: [
          { name: 'Blood Tests', icon: 'download.svg' },
          { name: 'CT Scans', icon: 'download.svg' },
          { name: 'Radiology Reports', icon: 'download.svg' },
          { name: 'X-Rays', icon: 'download.svg' },
          { name: 'Urine Test', icon: 'download.svg' }
        ]
      }
    }
  },
  methods: {
    selectPatient(id) {
      this.activePatient = id;
      // Dans une application réelle, vous feriez une requête API ici
      // pour récupérer les données du patient sélectionné
    }
  }
}
</script>

<style>
.app-container {
  display: flex;
  flex-direction: column;
  height: 100vh;
}

.main-container {
  display: flex;
  flex: 1;
  overflow: hidden;
}
</style>