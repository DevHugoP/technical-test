// components/dashboard/BloodPressureChart.vue
<template>
  <div class="chart-section">
    <div class="chart-header">
      <h3>Blood Pressure</h3>
      <div class="time-filter">
        <span>Last 6 months</span>
        <img src="@/assets/icons/chevron-down.svg" alt="Dropdown">
      </div>
    </div>
    
    <div class="chart-container">
      <canvas ref="bpChart"></canvas>
    </div>
    
    <div class="bp-indicators">
      <div class="bp-indicator">
        <div class="indicator-dot systolic"></div>
        <span>Systolic</span>
        <div class="bp-value">{{ chartData.systolic }}</div>
        <div class="bp-status high">Higher than Average</div>
      </div>
      
      <div class="bp-indicator">
        <div class="indicator-dot diastolic"></div>
        <span>Diastolic</span>
        <div class="bp-value">{{ chartData.diastolic }}</div>
        <div class="bp-status low">Lower than Average</div>
      </div>
    </div>
  </div>
</template>

<script>
import Chart from 'chart.js/auto'

export default {
  name: 'BloodPressureChart',
  props: {
    chartData: {
      type: Object,
      required: true
    }
  },
  mounted() {
    this.createChart()
  },
  methods: {
    createChart() {
      const ctx = this.$refs.bpChart.getContext('2d')
      
      const labels = this.chartData.history.map(item => item.month)
      const systolicData = this.chartData.history.map(item => item.systolic)
      const diastolicData = this.chartData.history.map(item => item.diastolic)
      
      new Chart(ctx, {
        type: 'line',
        data: {
          labels: labels,
          datasets: [
            {
              label: 'Systolic',
              data: systolicData,
              borderColor: '#D174E3',
              backgroundColor: '#D174E3',
              tension: 0.4,
              pointBackgroundColor: '#D174E3',
              pointRadius: 4
            },
            {
              label: 'Diastolic',
              data: diastolicData,
              borderColor: '#6A6DCD',
              backgroundColor: '#6A6DCD',
              tension: 0.4,
              pointBackgroundColor: '#6A6DCD',
              pointRadius: 4
            }
          ]
        },
        options: {
          responsive: true,
          maintainAspectRatio: false,
          scales: {
            y: {
              suggestedMin: 60,
              suggestedMax: 180,
              grid: {
                color: '#eee'
              }
            },
            x: {
              grid: {
                display: false
              }
            }
          },
          plugins: {
            legend: {
              display: false
            }
          }
        }
      })
    }
  }
}
</script>

<style scoped>
.chart-section {
  background-color: #f9f9f9;
  border-radius: 10px;
  padding: 1.5rem;
  margin-bottom: 2rem;
}

.chart-header {
  display: flex;
  justify-content: space-between;
  align-items: center;
  margin-bottom: 1rem;
}

.chart-header h3 {
  font-size: 1.1rem;
  font-weight: 600;
  color: #333;
}

.time-filter {
  display: flex;
  align-items: center;
  gap: 0.5rem;
  color: #666;
  cursor: pointer;
}

.chart-container {
  height: 200px;
  margin-bottom: 1rem;
}

.bp-indicators {
  display: flex;
  gap: 2rem;
}

.bp-indicator {
  display: flex;
  flex-direction: column;
  gap: 0.5rem;
}

.indicator-dot {
  width: 12px;
  height: 12px;
  border-radius: 50%;
  margin-bottom: 0.25rem;
}

.indicator-dot.systolic {
  background-color: #D174E3;
}

.indicator-dot.diastolic {
  background-color: #6A6DCD;
}

.bp-value {
  font-size: 1.5rem;
  font-weight: 700;
}

.bp-status {
  font-size: 0.8rem;
  display: flex;
  align-items: center;
}

.bp-status.high::before {
  content: '▲';
  margin-right: 0.25rem;
}

.bp-status.low::before {
  content: '▼';
  margin-right: 0.25rem;
}

.bp-status.high {
  color: #e74c3c;
}

.bp-status.low {
  color: #3498db;
}
</style>
