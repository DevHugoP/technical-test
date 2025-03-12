// components/dashboard/DiagnosticList.vue
<template>
  <div class="diagnostic-section">
    <h3 class="section-title">Diagnostic List</h3>
    
    <table class="diagnostic-table">
      <thead>
        <tr>
          <th>Problem/Diagnosis</th>
          <th>Description</th>
          <th>Status</th>
        </tr>
      </thead>
      <tbody>
        <tr v-for="(diagnosis, index) in diagnoses" :key="index">
          <td>{{ diagnosis.problem }}</td>
          <td>{{ diagnosis.description }}</td>
          <td>
            <span class="status-badge" :class="getStatusClass(diagnosis.status)">
              {{ diagnosis.status }}
            </span>
          </td>
        </tr>
      </tbody>
    </table>
  </div>
</template>

<script>
export default {
  name: 'DiagnosticList',
  props: {
    diagnoses: {
      type: Array,
      required: true
    }
  },
  methods: {
    getStatusClass(status) {
      if (status === 'Under Observation') return 'status-observation';
      if (status === 'Cured') return 'status-cured';
      if (status === 'Inactive') return 'status-inactive';
      return '';
    }
  }
}
</script>

<style scoped>
.diagnostic-section {
  margin-bottom: 2rem;
}

.section-title {
  font-size: 1.25rem;
  font-weight: 600;
  margin-bottom: 1rem;
  color: #333;
}

.diagnostic-table {
  width: 100%;
  border-collapse: collapse;
}

.diagnostic-table th {
  text-align: left;
  padding: 1rem;
  font-weight: 600;
  color: #333;
  border-bottom: 1px solid #eee;
}

.diagnostic-table td {
  padding: 1rem;
  border-bottom: 1px solid #eee;
}

.status-badge {
  display: inline-block;
  padding: 0.25rem 0.75rem;
  border-radius: 2rem;
  font-size: 0.8rem;
}

.status-observation {
  background-color: #e3f2fd;
  color: #2196f3;
}

.status-cured {
  background-color: #e8f5e9;
  color: #4caf50;
}

.status-inactive {
  background-color: #eeeeee;
  color: #757575;
}
</style>
