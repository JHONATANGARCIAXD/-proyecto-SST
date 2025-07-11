<script setup>
const healthData = {
  heartRate: {
    average: 72,
    min: 65,
    max: 85,
    trend: 'down' // 'up', 'down', 'stable'
  },
  activity: {
    steps: { 
      current: 5342, 
      goal: 10000,
      trend: 'up'
    },
    calories: { 
      current: 420, 
      goal: 600,
      trend: 'up'
    }
  },
  sedentary: {
    hours: 3.2,
    trend: 'down'
  },
  stress: {
    level: 'Medio',
    value: 65, // porcentaje
    trend: 'up'
  }
};

const getTrendIcon = (trend) => {
  return {
    'up': 'bi-arrow-up-circle-fill text-success',
    'down': 'bi-arrow-down-circle-fill text-danger',
    'stable': 'bi-dash-circle-fill text-secondary'
  }[trend] || 'bi-dash-circle-fill text-secondary';
};

const getStressColor = (level) => {
  return {
    'Bajo': 'bg-success',
    'Medio': 'bg-warning',
    'Alto': 'bg-danger'
  }[level] || 'bg-secondary';
};
</script>

<template>
  <div class="health-dashboard">
    <h2 class="dashboard-title">Mi Salud</h2>
    
    <div class="health-grid">
      <!-- Ritmo Cardiaco -->
      <div class="health-card">
        <div class="card-header">
          <i class="bi bi-heart-pulse"></i>
          <span>Ritmo Cardiaco</span>
        </div>
        <div class="card-content">
          <div class="heart-rate-chart">
            <div class="chart-placeholder">
              <span>📈 Gráfico de frecuencia cardiaca</span>
            </div>
            <div class="heart-rate-stats">
              <div class="rate-value">
                <span class="current-rate">{{ healthData.heartRate.average }}</span>
                <span class="rate-unit">BPM</span>
              </div>
              <div class="rate-range">
                <span class="min-rate">{{ healthData.heartRate.min }} min</span>
                <span class="max-rate">{{ healthData.heartRate.max }} max</span>
              </div>
              <i :class="['bi', getTrendIcon(healthData.heartRate.trend)]"></i>
            </div>
          </div>
          <div class="card-footer">
            <span>Promedio diario</span>
          </div>
        </div>
      </div>

      <!-- Actividad Física -->
      <div class="health-card">
        <div class="card-header">
          <i class="bi bi-activity"></i>
          <span>Actividad Física</span>
        </div>
        <div class="card-content">
          <!-- Pasos -->
          <div class="activity-metric">
            <div class="metric-header">
              <span>Pasos</span>
              <span class="completion">
                {{ Math.round((healthData.activity.steps.current / healthData.activity.steps.goal) * 100) }}%
              </span>
            </div>
            <div class="progress-container">
              <div class="progress-bar">
                <div class="progress-fill steps" 
                     :style="`width: ${(healthData.activity.steps.current / healthData.activity.steps.goal) * 100}%`">
                </div>
              </div>
              <div class="progress-labels">
                <span>{{ healthData.activity.steps.current.toLocaleString() }}</span>
                <span>{{ healthData.activity.steps.goal.toLocaleString() }}</span>
              </div>
            </div>
            
          </div>

          <!-- Calorías -->
          <div class="activity-metric">
            <div class="metric-header">
              <span>Calorías</span>
              <span class="completion">
                {{ Math.round((healthData.activity.calories.current / healthData.activity.calories.goal) * 100) }}%
              </span>
            </div>
            <div class="progress-container">
              <div class="progress-bar">
                <div class="progress-fill calories" 
                     :style="`width: ${(healthData.activity.calories.current / healthData.activity.calories.goal) * 100}%`">
                </div>
              </div>
              <div class="progress-labels">
                <span>{{ healthData.activity.calories.current }}</span>
                <span>{{ healthData.activity.calories.goal }}</span>
              </div>
            </div>
          
          </div>
        </div>
      </div>

      <!-- Tiempo Sedentario -->
      <div class="health-card">
        <div class="card-header">
          <i class="bi bi-hourglass"></i>
          <span>Tiempo Sedentario</span>
        </div>
        <div class="card-content">
          <div class="sedentary-chart">
            <div class="chart-placeholder">
              <span>📊 Gráfico de tiempo sedentario</span>
            </div>
            <div class="sedentary-stats">
              <div class="time-value">
                <span class="hours">{{ healthData.sedentary.hours }}</span>
                <span class="time-unit">horas</span>
              </div>
              <div class="time-recommendation">
                <span>Meta: &lt;2 horas</span>
              </div>
              <i :class="['bi', getTrendIcon(healthData.sedentary.trend)]"></i>
            </div>
          </div>
          <div class="card-footer">
            <span>Tiempo sentado hoy</span>
          </div>
        </div>
      </div>

      <!-- Nivel de Estrés -->
      <div class="health-card">
        <div class="card-header">
          <i class="bi bi-emoji-frown"></i>
          <span>Nivel de Estrés</span>
        </div>
        <div class="card-content">
          <div class="stress-gauge">
            <div class="gauge" :style="`--percentage: ${healthData.stress.value}%`">
              <div class="gauge-body">
                <div class="gauge-fill" :class="getStressColor(healthData.stress.level)"></div>
                <div class="gauge-cover">{{ healthData.stress.level }}</div>
              </div>
            </div>
            <div class="stress-info">
              <p>Basado en tu actividad y ritmo cardiaco</p>
              <i :class="['bi', getTrendIcon(healthData.stress.trend)]"></i>
            </div>
          </div>
        </div>
      </div>
    </div>
  </div>
</template>

<style scoped>
.health-dashboard {
  padding: 2rem;
  background-color: #f8f9fa;
  min-height: 100vh;
}

.dashboard-title {
  font-size: 1.8rem;
  font-weight: 700;
  color: #2c3e50;
  margin-bottom: 2rem;
}

.health-grid {
  display: grid;
  grid-template-columns: repeat(auto-fit, minmax(300px, 1fr));
  gap: 1.5rem;
}

.health-card {
  background: white;
  border-radius: 16px;
  box-shadow: 0 4px 12px rgba(0, 0, 0, 0.05);
  padding: 1.5rem;
  transition: transform 0.3s ease, box-shadow 0.3s ease;
}

.health-card:hover {
  transform: translateY(-5px);
  box-shadow: 0 8px 24px rgba(0, 0, 0, 0.1);
}

.card-header {
  display: flex;
  align-items: center;
  gap: 0.75rem;
  margin-bottom: 1.25rem;
  font-size: 1.1rem;
  font-weight: 600;
  color: #2c3e50;
}

.card-header i {
  font-size: 1.25rem;
  color: #0d6efd;
}

.card-content {
  height: calc(100% - 50px);
  display: flex;
  flex-direction: column;
}

.chart-placeholder {
  height: 150px;
  background-color: #f8f9fa;
  border-radius: 12px;
  display: flex;
  align-items: center;
  justify-content: center;
  color: #6c757d;
  margin-bottom: 1rem;
  border: 1px dashed #dee2e6;
}

.heart-rate-stats {
  display: flex;
  justify-content: space-between;
  align-items: center;
}

.rate-value {
  display: flex;
  align-items: baseline;
  gap: 0.5rem;
}

.current-rate {
  font-size: 2.5rem;
  font-weight: 700;
  color: #2c3e50;
}

.rate-unit {
  font-size: 1rem;
  color: #6c757d;
}

.rate-range {
  display: flex;
  gap: 1rem;
  font-size: 0.9rem;
  color: #6c757d;
}

.card-footer {
  margin-top: auto;
  font-size: 0.9rem;
  color: #6c757d;
}

.activity-metric {
  margin-bottom: 1.5rem;
  position: relative;
}

.activity-metric:last-child {
  margin-bottom: 0;
}

.metric-header {
  display: flex;
  justify-content: space-between;
  margin-bottom: 0.5rem;
  font-size: 0.95rem;
}

.completion {
  font-weight: 600;
  color: #2c3e50;
}

.progress-container {
  margin-bottom: 0.5rem;
}

.progress-bar {
  height: 8px;
  background-color: #e9ecef;
  border-radius: 4px;
  overflow: hidden;
  margin-bottom: 0.25rem;
}

.progress-fill {
  height: 100%;
  border-radius: 4px;
  transition: width 0.6s ease;
}

.progress-fill.steps {
  background: linear-gradient(90deg, #4facfe 0%, #00f2fe 100%);
}

.progress-fill.calories {
  background: linear-gradient(90deg, #ff7676 0%, #f54ea2 100%);
}

.progress-labels {
  display: flex;
  justify-content: space-between;
  font-size: 0.85rem;
  color: #6c757d;
}

.activity-metric i {
  position: absolute;
  right: 0;
  top: 0;
  font-size: 1.25rem;
}

.sedentary-stats {
  display: flex;
  justify-content: space-between;
  align-items: center;
}

.time-value {
  display: flex;
  align-items: baseline;
  gap: 0.5rem;
}

.hours {
  font-size: 2.5rem;
  font-weight: 700;
  color: #2c3e50;
}

.time-unit {
  font-size: 1rem;
  color: #6c757d;
}

.time-recommendation {
  font-size: 0.9rem;
  color: #6c757d;
}

.stress-gauge {
  display: flex;
  flex-direction: column;
  align-items: center;
  justify-content: center;
  height: 100%;
}

.gauge {
  --percentage: 0;
  --fill: #4facfe;
  width: 150px;
  height: 150px;
  margin: 0 auto 1rem;
}

.gauge-body {
  width: 100%;
  height: 100%;
  position: relative;
  border: 8px solid #f0f2f5;
  border-radius: 50%;
}

.gauge-fill {
  position: absolute;
  top: 0;
  left: 0;
  width: 100%;
  height: 100%;
  background: conic-gradient(var(--fill) calc(var(--percentage) * 1%), #f0f2f5 0);
  border-radius: 50%;
}

.gauge-fill.bg-success {
  --fill: #198754;
}

.gauge-fill.bg-warning {
  --fill: #ffc107;
}

.gauge-fill.bg-danger {
  --fill: #dc3545;
}

.gauge-cover {
  position: absolute;
  width: 75%;
  height: 75%;
  background: white;
  border-radius: 50%;
  top: 50%;
  left: 50%;
  transform: translate(-50%, -50%);
  display: flex;
  align-items: center;
  justify-content: center;
  font-size: 1.25rem;
  font-weight: 700;
  color: #2c3e50;
}

.stress-info {
  text-align: center;
  color: #6c757d;
  font-size: 0.9rem;
}

.stress-info i {
  font-size: 1.5rem;
  margin-top: 0.5rem;
}

/* Responsive adjustments */
@media (max-width: 768px) {
  .health-grid {
    grid-template-columns: 1fr;
  }
  
  .current-rate, .hours {
    font-size: 2rem;
  }
  
  .gauge {
    width: 120px;
    height: 120px;
  }
}
</style>