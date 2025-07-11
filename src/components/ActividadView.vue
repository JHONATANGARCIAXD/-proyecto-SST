<template>
  <div class="activity-dashboard">
    <h2 class="dashboard-title">Mi Actividad</h2>
    
    <div class="activity-grid">
      <!-- Historial de Actividades -->
      <div class="activity-card">
        <div class="card-header">
          <i class="bi bi-clock-history"></i>
          <span>Historial Reciente</span>
          <button class="view-all">Ver todo <i class="bi bi-chevron-right"></i></button>
        </div>
        <div class="card-content">
          <ul class="activity-list">
            <li v-for="(item, index) in activityData.history" :key="index">
              <div class="activity-item">
                <div class="activity-icon" :style="{ backgroundColor: getActivityColor(item.name) }">
                  <i :class="getActivityIcon(item.name)"></i>
                </div>
                <div class="activity-details">
                  <h4>{{ item.name }}</h4>
                  <p class="time">{{ item.time }}</p>
                </div>
                <span class="activity-points">
                  +{{ item.points }} pts
                </span>
              </div>
            </li>
          </ul>
        </div>
      </div>

      <!-- Estadísticas Semanales -->
      <div class="stats-card">
        <div class="card-header">
          <i class="bi bi-bar-chart"></i>
          <span>Tu Semana</span>
          <select class="time-filter">
            <option>Esta semana</option>
            <option>Semana pasada</option>
            <option>Este mes</option>
          </select>
        </div>
        <div class="card-content">
          <div class="stats-chart">
            <div class="chart-placeholder">
              <span>📈 Gráfico de tu actividad semanal</span>
            </div>
            <div class="stats-summary">
              <div class="stat-item">
                <span class="stat-value">12</span>
                <span class="stat-label">Pausas</span>
              </div>
              <div class="stat-item">
                <span class="stat-value">85%</span>
                <span class="stat-label">Metas</span>
              </div>
              <div class="stat-item">
                <span class="stat-value">320</span>
                <span class="stat-label">Puntos</span>
              </div>
            </div>
          </div>
        </div>
      </div>

      <!-- Logros -->
      <div class="achievements-card">
        <div class="card-header">
          <i class="bi bi-trophy"></i>
          <span>Tus Logros</span>
          <span class="progress">2/4 completados</span>
        </div>
        <div class="card-content">
          <div class="achievements-grid">
            <div class="achievement-item" v-for="(achievement, index) in activityData.achievements" :key="index">
              <div class="achievement-badge" :class="{ 'locked': achievement.icon === 'question' }">
                <div v-if="achievement.icon !== 'question'" class="achievement-icon" :style="{ color: achievement.color }">
                  <i :class="`bi bi-${achievement.icon === 'star' ? 'star-fill' : achievement.icon}`"></i>
                </div>
                <div v-else class="achievement-icon locked-icon">
                  <i class="bi bi-lock-fill"></i>
                </div>
              </div>
              <div class="achievement-info">
                <h5>{{ achievement.name }}</h5>
                <p>{{ achievement.description }}</p>
              </div>
            </div>
          </div>
        </div>
      </div>
    </div>
  </div>
</template>

<script setup>
const activityData = {
  history: [
    { name: "Estiramiento", time: "Hoy, 10:45 AM", points: 15 },
    { name: "Respiración", time: "Hoy, 09:30 AM", points: 10 },
    { name: "Caminata", time: "Ayer, 04:15 PM", points: 25 },
    { name: "Ejercicios", time: "Ayer, 02:00 PM", points: 10 }
  ],
  achievements: [
    { name: "Principiante", description: "Primera pausa completada", icon: "trophy", color: "#FFD700" },
    { name: "Constancia", description: "3 días consecutivos", icon: "award", color: "#C0C0C0" },
    { name: "Hidratación", description: "1L de agua en un día", icon: "star", color: "#cd7f32" },
    { name: "Experto", description: "5 días consecutivos", icon: "question", color: "#6c757d" }
  ]
};

const getActivityIcon = (activityName) => {
  const icons = {
    'Estiramiento': 'bi-arrow-repeat',
    'Respiración': 'bi-wind',
    'Caminata': 'bi-person-walking',
    'Ejercicios': 'bi-activity'
  };
  return `bi ${icons[activityName] || 'bi-check-circle'}`;
};

const getActivityColor = (activityName) => {
  const colors = {
    'Estiramiento': '#4facfe',
    'Respiración': '#00f2fe',
    'Caminata': '#43e97b',
    'Ejercicios': '#ff7eb3'
  };
  return colors[activityName] || '#6c757d';
};
</script>

<style scoped>
.activity-dashboard {
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

.activity-grid {
  display: grid;
  grid-template-columns: repeat(auto-fit, minmax(300px, 1fr));
  gap: 1.5rem;
}

.activity-card, .stats-card, .achievements-card {
  background: white;
  border-radius: 16px;
  box-shadow: 0 4px 12px rgba(0, 0, 0, 0.05);
  padding: 1.5rem;
  transition: transform 0.3s ease, box-shadow 0.3s ease;
}

.activity-card:hover, .stats-card:hover, .achievements-card:hover {
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

.view-all {
  margin-left: auto;
  background: none;
  border: none;
  color: #0d6efd;
  font-size: 0.9rem;
  display: flex;
  align-items: center;
  gap: 0.25rem;
  cursor: pointer;
}

.time-filter {
  margin-left: auto;
  border: 1px solid #dee2e6;
  border-radius: 50px;
  padding: 0.25rem 0.75rem;
  font-size: 0.85rem;
  color: #6c757d;
}

.progress {
  margin-left: auto;
  font-size: 0.9rem;
  color: #6c757d;
}

.activity-list {
  list-style: none;
  padding: 0;
  margin: 0;
}

.activity-item {
  display: flex;
  align-items: center;
  gap: 1rem;
  padding: 1rem 0;
  border-bottom: 1px solid #f0f0f0;
}

.activity-item:last-child {
  border-bottom: none;
}

.activity-icon {
  width: 40px;
  height: 40px;
  border-radius: 50%;
  display: flex;
  align-items: center;
  justify-content: center;
  color: white;
}

.activity-icon i {
  font-size: 1.25rem;
}

.activity-details {
  flex: 1;
}

.activity-details h4 {
  margin: 0;
  font-size: 1rem;
  color: #2c3e50;
}

.time {
  margin: 0;
  font-size: 0.85rem;
  color: #6c757d;
}

.activity-points {
  background: linear-gradient(135deg, #00f2fe 0%, #4facfe 100%);
  color: white;
  padding: 0.35rem 0.75rem;
  border-radius: 50px;
  font-size: 0.85rem;
  font-weight: 600;
}

.stats-chart {
  display: flex;
  flex-direction: column;
  height: 100%;
}

.chart-placeholder {
  height: 180px;
  background-color: #f8f9fa;
  border-radius: 12px;
  display: flex;
  align-items: center;
  justify-content: center;
  color: #6c757d;
  margin-bottom: 1rem;
  border: 1px dashed #dee2e6;
}

.stats-summary {
  display: grid;
  grid-template-columns: repeat(3, 1fr);
  gap: 1rem;
  margin-top: auto;
}

.stat-item {
  background-color: #f8f9fa;
  border-radius: 12px;
  padding: 0.75rem;
  text-align: center;
}

.stat-value {
  font-size: 1.25rem;
  font-weight: 700;
  color: #2c3e50;
  display: block;
}

.stat-label {
  font-size: 0.85rem;
  color: #6c757d;
  display: block;
}

.achievements-grid {
  display: grid;
  grid-template-columns: repeat(auto-fit, minmax(200px, 1fr));
  gap: 1rem;
}

.achievement-item {
  display: flex;
  align-items: center;
  gap: 1rem;
  padding: 1rem;
  background-color: #f8f9fa;
  border-radius: 12px;
}

.achievement-badge {
  width: 50px;
  height: 50px;
  border-radius: 50%;
  background-color: white;
  display: flex;
  align-items: center;
  justify-content: center;
  position: relative;
  box-shadow: 0 4px 8px rgba(0, 0, 0, 0.05);
}

.achievement-badge.locked {
  background-color: #e9ecef;
}

.achievement-icon {
  font-size: 1.5rem;
}

.locked-icon {
  color: #6c757d;
}

.achievement-info h5 {
  margin: 0 0 0.25rem;
  font-size: 1rem;
  color: #2c3e50;
}

.achievement-info p {
  margin: 0;
  font-size: 0.85rem;
  color: #6c757d;
}

/* Responsive adjustments */
@media (max-width: 768px) {
  .activity-grid {
    grid-template-columns: 1fr;
  }
  
  .stats-summary {
    grid-template-columns: 1fr;
  }
  
  .achievements-grid {
    grid-template-columns: 1fr 1fr;
  }
}

@media (max-width: 480px) {
  .achievements-grid {
    grid-template-columns: 1fr;
  }
}
</style>