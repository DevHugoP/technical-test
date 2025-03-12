// components/layout/TechCareHeader.vue
<template>
  <header class="header">
    <div class="logo">
      <img src="@/assets/logo.svg" alt="Tech Care Logo">
      <h1>Tech Care</h1>
    </div>
    
    <nav class="main-nav">
      <BaseNavItem icon="home.svg" label="Overview" :active="false" />
      <BaseNavItem icon="users.svg" label="Patients" :active="true" />
      <BaseNavItem icon="calendar.svg" label="Schedule" :active="false" />
      <BaseNavItem icon="message.svg" label="Message" :active="false" />
      <BaseNavItem icon="dollar.svg" label="Transactions" :active="false" />
    </nav>
    
    <div class="user-profile">
      <div class="user-info">
        <img src="@/assets/doctor-profile.jpg" alt="Dr. Jose Simmons">
        <div>
          <p class="doctor-name">Dr. Jose Simmons</p>
          <p class="doctor-title">General Practitioner</p>
        </div>
      </div>
      <div class="settings">
        <BaseIconButton icon="settings.svg" />
        <BaseIconButton icon="more.svg" />
      </div>
    </div>
  </header>
</template>

<script>
import BaseIconButton from '../base/BaseIconButton.vue';
import BaseNavItem from '../base/BaseNavItem.vue';

export default {
  name: 'TechCareHeader',
  components: {
    BaseNavItem,
    BaseIconButton
  }
}
</script>

<style scoped>
.header {
  display: flex;
  align-items: center;
  padding: 0 2rem;
  height: 70px;
  background-color: white;
  box-shadow: 0 2px 4px rgba(0, 0, 0, 0.05);
}

.logo {
  display: flex;
  align-items: center;
  margin-right: 2rem;
}

.logo img {
  height: 40px;
  margin-right: 0.5rem;
}

.logo h1 {
  font-size: 1.5rem;
  font-weight: 700;
  color: #333;
}

.main-nav {
  display: flex;
  flex: 1;
  gap: 1rem;
}

.user-profile {
  display: flex;
  align-items: center;
  gap: 1rem;
}

.user-info {
  display: flex;
  align-items: center;
  gap: 0.5rem;
}

.user-info img {
  width: 40px;
  height: 40px;
  border-radius: 50%;
  object-fit: cover;
}

.doctor-name {
  font-weight: 600;
  font-size: 0.9rem;
}

.doctor-title {
  font-size: 0.8rem;
  color: #666;
}

.settings {
  display: flex;
  gap: 0.5rem;
}
</style>
