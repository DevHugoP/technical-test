// components/dashboard/PatientInfoSidebar.vue
<template>
  <div class="patient-sidebar">
    <div class="patient-profile">
      <div class="profile-image">
        <img src="@/assets/user.png" :alt="patient.name">
      </div>
      
      <h2 class="patient-name">{{ patient.name }}</h2>
      
      <div class="patient-details">
        <div class="detail-item">
          <div class="detail-icon">
            <img src="@/assets/icons/calendar.svg" alt="Date of birth">
          </div>
          <div class="detail-content">
            <span class="detail-label">Date Of Birth</span>
            <span class="detail-value">{{ patient.dateOfBirth }}</span>
          </div>
        </div>
        
        <div class="detail-item">
          <div class="detail-icon">
            <img src="@/assets/icons/female.svg" alt="Gender">
          </div>
          <div class="detail-content">
            <span class="detail-label">Gender</span>
            <span class="detail-value">{{ patient.gender }}</span>
          </div>
        </div>
        
        <div class="detail-item">
          <div class="detail-icon">
            <img src="@/assets/icons/phone.svg" alt="Contact">
          </div>
          <div class="detail-content">
            <span class="detail-label">Contact Info</span>
            <span class="detail-value">{{ patient.contact }}</span>
          </div>
        </div>
        
        <div class="detail-item">
          <div class="detail-icon">
            <img src="@/assets/icons/phone.svg" alt="Emergency">
          </div>
          <div class="detail-content">
            <span class="detail-label">Emergency Contacts</span>
            <span class="detail-value">{{ patient.emergency }}</span>
          </div>
        </div>
        
        <div class="detail-item">
          <div class="detail-icon">
            <img src="@/assets/icons/shield.svg" alt="Insurance">
          </div>
          <div class="detail-content">
            <span class="detail-label">Insurance Provider</span>
            <span class="detail-value">{{ patient.insurance }}</span>
          </div>
        </div>
      </div>
      
      <button class="info-button">Show All Information</button>
    </div>
    
    <div class="lab-results">
      <h3 class="section-title">Lab Results</h3>
      
      <ul class="results-list">
        <li v-for="(result, index) in labResults" :key="index" class="result-item">
          <span class="result-name">{{ result.name }}</span>
          <img :src="(`@/assets/icons/${result.icon}`)" alt="Download" class="download-icon">
        </li>
      </ul>
    </div>
  </div>
</template>

<script>
export default {
  name: 'PatientInfoSidebar',
  props: {
    patient: {
      type: Object,
      required: true
    },
    labResults: {
      type: Array,
      required: true
    }
  }
}
</script>

<style scoped>
.patient-sidebar {
  width: 300px;
  background-color: white;
  padding: 2rem;
  display: flex;
  flex-direction: column;
  border-left: 1px solid #eee;
}

.profile-image {
  width: 120px;
  height: 120px;
  border-radius: 50%;
  overflow: hidden;
  margin: 0 auto 1.5rem;
}

.profile-image img {
  width: 100%;
  height: 100%;
  object-fit: cover;
}

.patient-name {
  font-size: 1.5rem;
  font-weight: 600;
  text-align: center;
  margin-bottom: 2rem;
}

.patient-details {
  display: flex;
  flex-direction: column;
  gap: 1.25rem;
  margin-bottom: 2rem;
}

.detail-item {
  display: flex;
  align-items: flex-start;
  gap: 0.75rem;
}

.detail-icon {
  width: 40px;
  height: 40px;
  border-radius: 50%;
  background-color: #f2f2f2;
  display: flex;
  align-items: center;
  justify-content: center;
}

.detail-icon img {
  width: 20px;
  height: 20px;
}

.detail-content {
  display: flex;
  flex-direction: column;
}

.detail-label {
  font-size: 0.8rem;
  color: #666;
  margin-bottom: 0.25rem;
}

.detail-value {
  font-weight: 500;
}

.info-button {
  background-color: #4BD6B9;
  color: white;
  border: none;
  border-radius: 2rem;
  padding: 0.75rem 1.5rem;
  font-weight: 500;
  cursor: pointer;
  margin-top: 0.5rem;
  transition: background-color 0.2s;
}

.info-button:hover {
  background-color: #3dc0a4;
}

.lab-results {
  margin-top: 2rem;
}

.section-title {
  font-size: 1.25rem;
  font-weight: 600;
  margin-bottom: 1rem;
}

.results-list {
  list-style: none;
  padding: 0;
  display: flex;
  flex-direction: column;
  gap: 1rem;
}

.result-item {
  display: flex;
  justify-content: space-between;
  align-items: center;
  padding: 0.75rem 1rem;
  background-color: #f9f9f9;
  border-radius: 0.5rem;
}

.download-icon {
  width: 20px;
  height: 20px;
  cursor: pointer;
}
</style>