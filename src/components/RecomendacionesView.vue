<script setup>
const recommendations = {
  activeBreak: {
    title: "Estiramiento de Espalda",
    description: "Realiza estiramientos suaves para aliviar la tensión en tu espalda después de largas horas sentado.",
    icon: "bi-activity",
    duration: "3 min",
    benefit: "Alivia tensión lumbar",
    completed: false
  },
  personalized: [
    { 
      text: "Bebe más agua (has consumido 1L de 2L hoy)", 
      icon: "bi-cup",
      progress: 50,
      action: "Beber ahora",
      completed: false
    },
    { 
      text: "Camina 5 minutos cada hora", 
      icon: "bi-person-walking",
      progress: 30,
      action: "Iniciar caminata",
      completed: false
    },
    { 
      text: "Intenta dormir 8 horas esta noche", 
      icon: "bi-moon",
      progress: 0,
      action: "Programar sueño",
      completed: false
    }
  ],
  dailyStats: {
    pausasCompletadas: 3,
    pausasPendientes: 2,
    aguaConsumida: 1.2,
    aguaMeta: 2,
    actividad: 65 // porcentaje
  }
};
</script>

<template>
  <div class="recommendations-dashboard">
    <h2 class="dashboard-title">Recomendaciones para ti</h2>
    
    <div class="recommendations-grid">
      <!-- Pausa Activa Recomendada -->
      <div class="recommendation-card highlight">
        <div class="card-header">
          <i class="bi bi-clock"></i>
          <span>Pausa Activa Recomendada</span>
        </div>
        <div class="card-content">
          <div class="recommendation-icon">
            <i :class="['bi', recommendations.activeBreak.icon]"></i>
          </div>
          <h3>{{ recommendations.activeBreak.title }}</h3>
          <p class="description">{{ recommendations.activeBreak.description }}</p>
          
          <div class="recommendation-details">
            <div class="detail-item">
              <i class="bi bi-stopwatch"></i>
              <span>{{ recommendations.activeBreak.duration }}</span>
            </div>
            <div class="detail-item">
              <i class="bi bi-heart"></i>
              <span>{{ recommendations.activeBreak.benefit }}</span>
            </div>
          </div>
          
          <button class="action-button">
            {{ recommendations.activeBreak.completed ? 'Completado' : 'Iniciar Pausa' }}
            <i class="bi" :class="recommendations.activeBreak.completed ? 'bi-check-circle' : 'bi-play-circle'"></i>
          </button>
        </div>
      </div>

      <!-- Recomendaciones Personalizadas -->
      <div class="recommendation-card">
        <div class="card-header">
          <i class="bi bi-person"></i>
          <span>Personalizadas para ti</span>
        </div>
        <div class="card-content">
          <ul class="recommendation-list">
            <li v-for="(item, index) in recommendations.personalized" :key="index">
              <div class="recommendation-item">
                <div class="item-icon">
                  <i :class="['bi', item.icon]"></i>
                </div>
                <div class="item-content">
                  <p>{{ item.text }}</p>
                  <div class="progress-container">
                    <div class="progress-bar">
                      <div class="progress-fill" :style="`width: ${item.progress}%`"></div>
                    </div>
                    <span>{{ item.progress }}%</span>
                  </div>
                </div>
                <button class="item-action">
                  {{ item.action }}
                </button>
              </div>
            </li>
          </ul>
        </div>
      </div>

      <!-- Estadísticas del Día -->
      <div class="stats-card">
        <div class="card-header">
          <i class="bi bi-graph-up"></i>
          <span>Tu progreso hoy</span>
        </div>
        <div class="card-content">
          <div class="stats-grid">
            <!-- Pausas -->
            <div class="stat-item">
              <div class="stat-value">
                {{ recommendations.dailyStats.pausasCompletadas }}
                <small>/{{ recommendations.dailyStats.pausasCompletadas + recommendations.dailyStats.pausasPendientes }}</small>
              </div>
              <div class="stat-label">
                <i class="bi bi-check-circle"></i>
                <span>Pausas completadas</span>
              </div>
            </div>
            
            <!-- Agua -->
            <div class="stat-item">
              <div class="stat-value">
                {{ recommendations.dailyStats.aguaConsumida.toFixed(1) }}
                <small>/{{ recommendations.dailyStats.aguaMeta }}L</small>
              </div>
              <div class="stat-label">
                <i class="bi bi-cup"></i>
                <span>Agua consumida</span>
              </div>
            </div>
            
            <!-- Actividad -->
            <div class="stat-item">
              <div class="stat-value">
                {{ recommendations.dailyStats.actividad }}%
              </div>
              <div class="stat-label">
                <i class="bi bi-activity"></i>
                <span>Nivel de actividad</span>
              </div>
            </div>
          </div>
          
          <div class="chart-placeholder">
            <span>📈 Visualización de tu progreso diario</span>
          </div>
        </div>
      </div>
    </div>
  </div>
</template>

<style scoped>
.recommendations-dashboard {
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

.recommendations-grid {
  display: grid;
  grid-template-columns: repeat(auto-fit, minmax(300px, 1fr));
  gap: 1.5rem;
}

.recommendation-card, .stats-card {
  background: white;
  border-radius: 16px;
  box-shadow: 0 4px 12px rgba(0, 0, 0, 0.05);
  padding: 1.5rem;
  transition: transform 0.3s ease, box-shadow 0.3s ease;
}

.recommendation-card:hover, .stats-card:hover {
  transform: translateY(-5px);
  box-shadow: 0 8px 24px rgba(0, 0, 0, 0.1);
}

.recommendation-card.highlight {
  background: linear-gradient(135deg, #f5f7fa 0%, #e4e8ed 100%);
  border: 1px solid rgba(13, 110, 253, 0.1);
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

.recommendation-icon {
  width: 80px;
  height: 80px;
  background-color: rgba(13, 110, 253, 0.1);
  border-radius: 50%;
  display: flex;
  align-items: center;
  justify-content: center;
  margin: 0 auto 1.5rem;
}

.recommendation-icon i {
  font-size: 2.5rem;
  color: #0d6efd;
}

h3 {
  font-size: 1.5rem;
  font-weight: 700;
  color: #2c3e50;
  text-align: center;
  margin-bottom: 1rem;
}

.description {
  color: #6c757d;
  text-align: center;
  margin-bottom: 1.5rem;
}

.recommendation-details {
  display: flex;
  justify-content: center;
  gap: 2rem;
  margin-bottom: 1.5rem;
}

.detail-item {
  display: flex;
  align-items: center;
  gap: 0.5rem;
  font-size: 0.95rem;
  color: #6c757d;
}

.detail-item i {
  color: #0d6efd;
}

.action-button {
  display: flex;
  align-items: center;
  justify-content: center;
  gap: 0.5rem;
  width: 100%;
  background: linear-gradient(to right, #0d6efd, #0b5ed7);
  color: white;
  border: none;
  padding: 0.75rem;
  border-radius: 50px;
  font-weight: 600;
  margin-top: 1rem;
  cursor: pointer;
  transition: transform 0.2s ease;
}

.action-button:hover {
  transform: translateY(-2px);
}

.recommendation-list {
  list-style: none;
  padding: 0;
  margin: 0;
}

.recommendation-item {
  display: flex;
  align-items: center;
  gap: 1rem;
  padding: 1rem 0;
  border-bottom: 1px solid #f0f0f0;
}

.recommendation-item:last-child {
  border-bottom: none;
}

.item-icon {
  width: 40px;
  height: 40px;
  background-color: rgba(13, 110, 253, 0.1);
  border-radius: 50%;
  display: flex;
  align-items: center;
  justify-content: center;
}

.item-icon i {
  color: #0d6efd;
  font-size: 1.25rem;
}

.item-content {
  flex: 1;
}

.item-content p {
  margin: 0 0 0.5rem;
  color: #2c3e50;
  font-weight: 500;
}

.progress-container {
  display: flex;
  align-items: center;
  gap: 0.5rem;
}

.progress-bar {
  flex: 1;
  height: 6px;
  background-color: #e9ecef;
  border-radius: 3px;
  overflow: hidden;
}

.progress-fill {
  height: 100%;
  background: linear-gradient(90deg, #4facfe 0%, #00f2fe 100%);
  border-radius: 3px;
  transition: width 0.6s ease;
}

.progress-container span {
  font-size: 0.85rem;
  color: #6c757d;
  font-weight: 600;
}

.item-action {
  background: none;
  border: 1px solid #0d6efd;
  color: #0d6efd;
  padding: 0.35rem 0.75rem;
  border-radius: 50px;
  font-size: 0.85rem;
  font-weight: 600;
  cursor: pointer;
  transition: all 0.2s ease;
}

.item-action:hover {
  background-color: rgba(13, 110, 253, 0.1);
}

.stats-grid {
  display: grid;
  grid-template-columns: repeat(2, 1fr);
  gap: 1rem;
  margin-bottom: 1.5rem;
}

.stat-item {
  background-color: #f8f9fa;
  border-radius: 12px;
  padding: 1rem;
  text-align: center;
}

.stat-value {
  font-size: 1.5rem;
  font-weight: 700;
  color: #2c3e50;
  margin-bottom: 0.5rem;
}

.stat-value small {
  font-size: 0.9rem;
  color: #6c757d;
  font-weight: 400;
}

.stat-label {
  display: flex;
  align-items: center;
  justify-content: center;
  gap: 0.5rem;
  font-size: 0.9rem;
  color: #6c757d;
}

.stat-label i {
  color: #0d6efd;
}

.chart-placeholder {
  height: 200px;
  background-color: #f8f9fa;
  border-radius: 12px;
  display: flex;
  align-items: center;
  justify-content: center;
  color: #6c757d;
  border: 1px dashed #dee2e6;
}

/* Responsive adjustments */
@media (max-width: 768px) {
  .recommendations-grid {
    grid-template-columns: 1fr;
  }
  
  .stats-grid {
    grid-template-columns: 1fr;
  }
  
  .recommendation-item {
    flex-direction: column;
    align-items: flex-start;
  }
  
  .item-action {
    width: 100%;
    margin-top: 0.5rem;
  }
}
</style>