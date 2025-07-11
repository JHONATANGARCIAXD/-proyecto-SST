<script setup>
const stats = {
  pausas: {
    completadas: 5,
    pendientes: 2,
    meta: 8,
    tendencia: 'up' // 'up' or 'down'
  },
  puntos: {
    total: 1247,
    hoy: 25,
    tendencia: 'up'
  },
  productividad: {
    valor: 1246,
    eficiencia: "Alta Focus",
    nivel: 85 // porcentaje
  },
  salud: {
    bpm: 72,
    estado: "Normal",
    poder: 6847,
    tendencia: 'stable' // 'up', 'down', 'stable'
  }
};

const getTrendIcon = (tendencia) => {
  return {
    'up': 'bi-graph-up-arrow text-success',
    'down': 'bi-graph-down-arrow text-danger',
    'stable': 'bi-dash-circle text-secondary'
  }[tendencia] || 'bi-dash-circle text-secondary';
};
</script>

<template>
  <div class="dashboard-container">
    <h2 class="dashboard-title">Mi Dashboard</h2>

    <div class="stats-grid">
      <!-- Tarjeta de Pausas -->
      <div class="stat-card">
        <div class="card-header">
          <i class="bi bi-clock-history"></i>
          <span>Pausas Activas</span>
        </div>
        <div class="card-content">
          <div class="main-stat">
            <span class="stat-value">{{ stats.pausas.completadas }}</span>
            <span class="stat-divider">/</span>
            <span class="stat-value">{{ stats.pausas.meta }}</span>
            <i :class="['bi', getTrendIcon(stats.pausas.tendencia)]"></i>
          </div>
          <div class="progress-container">
            <div class="progress-label">
              <span>Completadas: {{ stats.pausas.completadas }}</span>
              <span>Pendientes: {{ stats.pausas.pendientes }}</span>
            </div>
            <div class="progress-bar">
              <div class="progress-fill" :style="`width: ${(stats.pausas.completadas / stats.pausas.meta) * 100}%`">
              </div>
            </div>
          </div>
        </div>
      </div>

      <!-- Tarjeta de Puntos -->
      <div class="stat-card highlight">
        <div class="card-header">
          <i class="bi bi-star-fill"></i>
          <span>Mis Puntos</span>
        </div>
        <div class="card-content">
          <div class="main-stat">
            <span class="stat-value">{{ stats.puntos.total.toLocaleString() }}</span>
            <i :class="['bi', getTrendIcon(stats.puntos.tendencia)]"></i>
          </div>
          <div class="secondary-stat">
            <span class="badge-success">
              +{{ stats.puntos.hoy }} hoy
            </span>
          </div>
          <button class="action-button">
            Canjear Recompensas
            <i class="bi bi-arrow-right"></i>
          </button>
        </div>
      </div>

      <!-- Tarjeta de Productividad -->
      <div class="stat-card">
        <div class="card-header">
          <i class="bi bi-speedometer2"></i>
          <span>Productividad</span>
        </div>
        <div class="card-content">
          <div class="gauge-container">
            <div class="gauge" :style="`--percentage: ${stats.productividad.nivel}%`">
              <div class="gauge-body">
                <div class="gauge-fill"></div>
                <div class="gauge-cover">{{ stats.productividad.nivel }}%</div>
              </div>
            </div>
          </div>
          <div class="productivity-info">
            <span class="efficiency">{{ stats.productividad.eficiencia }}</span>
            <span class="score">{{ stats.productividad.valor.toLocaleString() }} pts</span>
          </div>
        </div>
      </div>

      <!-- Tarjeta de Salud -->
      <div class="stat-card">
        <div class="card-header">
          <i class="bi bi-heart-pulse"></i>
          <span>Salud</span>
        </div>
        <div class="card-content health-content">
          <div class="health-metric">
            <div class="metric-value">
              <span>{{ stats.salud.bpm }}</span>
              <small>BPM</small>
            </div>
            <span :class="`status-badge ${stats.salud.estado.toLowerCase()}`">
              {{ stats.salud.estado }}
            </span>
          </div>
          <div class="health-metric">
            <div class="metric-value">
              <span>{{ stats.salud.poder.toLocaleString() }}</span>
              <small>Poder</small>
            </div>
            <i :class="['bi', getTrendIcon(stats.salud.tendencia)]"></i>
          </div>
        </div>
      </div>
    </div>
  </div>
</template>

<style scoped>
.dashboard-container {
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

.stats-grid {
  display: grid;
  grid-template-columns: repeat(auto-fit, minmax(280px, 1fr));
  gap: 1.5rem;
}

.stat-card {
  background: white;
  border-radius: 16px;
  box-shadow: 0 4px 12px rgba(0, 0, 0, 0.05);
  padding: 1.5rem;
  transition: transform 0.3s ease, box-shadow 0.3s ease;
}

.stat-card:hover {
  transform: translateY(-5px);
  box-shadow: 0 8px 24px rgba(0, 0, 0, 0.1);
}

.stat-card.highlight {
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

.main-stat {
  display: flex;
  align-items: center;
  gap: 0.5rem;
  margin-bottom: 1rem;
}

.stat-value {
  font-size: 2.5rem;
  font-weight: 700;
  color: #2c3e50;
}

.stat-divider {
  font-size: 1.5rem;
  color: #adb5bd;
}

.progress-container {
  margin-top: 1.5rem;
}

.progress-label {
  display: flex;
  justify-content: space-between;
  font-size: 0.85rem;
  color: #6c757d;
  margin-bottom: 0.5rem;
}

.progress-bar {
  height: 8px;
  background-color: #e9ecef;
  border-radius: 4px;
  overflow: hidden;
}

.progress-fill {
  height: 100%;
  background: linear-gradient(90deg, #4facfe 0%, #00f2fe 100%);
  border-radius: 4px;
  transition: width 0.6s ease;
}

.secondary-stat {
  margin: 1rem 0;
}

.badge-success {
  background-color: rgba(25, 135, 84, 0.1);
  color: #198754;
  padding: 0.35rem 0.75rem;
  border-radius: 50px;
  font-size: 0.85rem;
  font-weight: 600;
}

.action-button {
  display: flex;
  align-items: center;
  gap: 0.5rem;
  background: linear-gradient(to right, #0d6efd, #0b5ed7);
  color: white;
  border: none;
  padding: 0.75rem 1.25rem;
  border-radius: 50px;
  font-weight: 600;
  margin-top: 1rem;
  cursor: pointer;
  transition: transform 0.2s ease;
}

.action-button:hover {
  transform: translateY(-2px);
}

.gauge-container {
  margin: 1rem 0;
}

.gauge {
  --percentage: 0;
  --fill: #4facfe;
  width: 120px;
  height: 120px;
  margin: 0 auto;
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
  font-size: 1.5rem;
  font-weight: 700;
  color: #2c3e50;
}

.productivity-info {
  display: flex;
  justify-content: space-between;
  align-items: center;
  margin-top: 1rem;
}

.efficiency {
  font-size: 1.1rem;
  font-weight: 600;
  color: #2c3e50;
}

.score {
  background-color: rgba(13, 110, 253, 0.1);
  color: #0d6efd;
  padding: 0.35rem 0.75rem;
  border-radius: 50px;
  font-size: 0.85rem;
  font-weight: 600;
}

.health-content {
  display: flex;
  justify-content: space-between;
}

.health-metric {
  display: flex;
  flex-direction: column;
  align-items: center;
}

.metric-value {
  display: flex;
  align-items: baseline;
  gap: 0.25rem;
  margin-bottom: 0.5rem;
}

.metric-value span {
  font-size: 2rem;
  font-weight: 700;
  color: #2c3e50;
}

.metric-value small {
  font-size: 0.9rem;
  color: #6c757d;
}

.status-badge {
  padding: 0.35rem 0.75rem;
  border-radius: 50px;
  font-size: 0.85rem;
  font-weight: 600;
}

.status-badge.normal {
  background-color: rgba(25, 135, 84, 0.1);
  color: #198754;
}

.status-badge.alto {
  background-color: rgba(220, 53, 69, 0.1);
  color: #dc3545;
}

.status-badge.bajo {
  background-color: rgba(255, 193, 7, 0.1);
  color: #ffc107;
}

/* Responsive adjustments */
@media (max-width: 768px) {
  .stats-grid {
    grid-template-columns: 1fr;
  }

  .health-content {
    flex-direction: column;
    gap: 1.5rem;
  }
}
</style>