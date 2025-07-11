<script setup>
const rewardsData = {
  individual: {
    points: 1247,
    nextReward: {
      needed: 753,
      total: 2000
    }
  },
  team: {
    name: "Desarrollo Frontend",
    goal: 10000,
    progress: 45,
    members: [
      { name: "Tú", points: 1247 },
      { name: "María", points: 1089 },
      { name: "Carlos", points: 987 },
      { name: "Ana", points: 756 }
    ]
  }
};
const lowCostRewards = [
  { title: "Café Gratis", description: "Disfruta de tu bebida favorita", points: 50, icon: "cup-fill", color: "warning" },
  { title: "Acceso Prioritario", description: "Evita las filas en hora pico", points: 100, icon: "clock-fill", color: "info" },
  { title: "Reconocimiento Digital", description: "Aparece en el muro interno", points: 75, icon: "trophy-fill", color: "success" }
];

const midCostRewards = [
  { title: "Medio Día Libre", description: "Descansa y disfruta tu tiempo", points: 500, icon: "sun-fill", color: "danger" },
  { title: "Bono Apps Comida", description: "$20 USD para delivery", points: 400, icon: "egg-fried", color: "primary" },
  { title: "Entrada a Rifa", description: "Participa por premios increíbles", points: 300, icon: "gift-fill", color: "purple" }
];
</script>

<template>
  <div class="bg-white min-vh-100 p-4">
    <h1 class="text-center mb-4 text-primary fw-bold">Recompensas</h1>

    <!-- Puntos Individuales -->
    <div class="row g-4 mb-5">
      <div class="col-md-6">
        <div class="card h-100 border-0 shadow-sm hover-card">
          <div class="card-header border-0 bg-transparent fw-semibold text-dark">
            Puntos Individuales
          </div>
          <div class="card-body d-flex flex-column">
            <h3 class="display-6 fw-bold text-dark">{{ rewardsData.individual.points.toLocaleString() }}</h3>
            <p class="stat-label">Puntos totales</p>

            <div class="mb-4 mt-3">
              <h5 class="text-dark">Próxima recompensa</h5>
              <div class="d-flex justify-content-between">
                <span class="text-secondary">
                  {{ rewardsData.individual.nextReward.needed }} / {{ rewardsData.individual.nextReward.total }}
                </span>
                <span class="text-secondary">
                  {{ Math.round((rewardsData.individual.points / rewardsData.individual.nextReward.total) * 100) }}%
                </span>
              </div>
              <div class="progress mt-2">
                <div class="progress-bar bg-warning"
                  :style="`width: ${(rewardsData.individual.points / rewardsData.individual.nextReward.total) * 100}%`">
                </div>
              </div>
            </div>

            <div class="alert alert-info d-flex align-items-center bg-info bg-opacity-10 border-info text-dark mt-auto">
              <i class="bi bi-info-circle me-2 text-info"></i>
              Necesitas {{ rewardsData.individual.nextReward.needed }} puntos más para desbloquear tu próxima
              recompensa.
            </div>
          </div>
        </div>
      </div>

      <!-- Progreso del Equipo -->
      <div class="col-md-6">
        <div class="card h-100 border-0 shadow-sm hover-card">
          <div class="card-header border-0 bg-transparent fw-semibold text-dark">
            Progreso del Equipo
          </div>
          <div class="card-body d-flex flex-column">
            <h5 class="mb-3 text-dark">{{ rewardsData.team.name }}</h5>

            <div class="mb-4">
              <div class="d-flex justify-content-between mb-1">
                <span class="text-secondary">Meta del equipo: {{ rewardsData.team.goal.toLocaleString() }} pts</span>
                <span class="text-dark">{{ rewardsData.team.progress }}%</span>
              </div>
              <div class="progress">
                <div class="progress-bar bg-success" :style="`width: ${rewardsData.team.progress}%`"></div>
              </div>
            </div>

            <h6 class="mb-3 text-dark">Miembros del equipo</h6>
            <ul class="list-group list-group-flush mt-auto">
              <li
                class="list-group-item bg-white d-flex justify-content-between align-items-center text-dark border-light"
                v-for="member in rewardsData.team.members" :key="member.name">
                {{ member.name }}
                <span class="badge bg-primary rounded-pill text-white">{{ member.points.toLocaleString() }} pts</span>
              </li>
            </ul>
          </div>
        </div>
      </div>
    </div>

    <!-- Recompensas Individuales -->
    <div class="mb-5">
      <h2 class="mb-3 d-flex align-items-center gap-2">
        <i class="bi bi-stars text-warning"></i>
        <span class="text-dark">Recompensas Individuales</span>
      </h2>

      <!-- Bajo Costo -->
      <h5 class="fw-bold text-dark mb-3 d-flex align-items-center gap-2">
        <i class="bi bi-cup-hot text-warning"></i>
        <span>Bajo Costo</span>
      </h5>
      <div class="row g-4 mb-4">
        <div class="col-md-4" v-for="reward in lowCostRewards" :key="reward.title">
          <div class="card h-100 border-0 shadow-sm hover-card">
            <div class="card-body d-flex flex-column p-4">
              <div class="d-flex align-items-center mb-3">
                <div
                  :class="`bg-${reward.color} bg-opacity-10 d-flex align-items-center justify-content-center rounded-circle me-3`"
                  style="width: 48px; height: 48px;">
                  <i :class="`bi bi-${reward.icon} text-${reward.color}`" style="font-size: 1.5rem;"></i>
                </div>
                <h5 class="card-title mb-0 text-dark">{{ reward.title }}</h5>
              </div>
              <p class="card-text text-secondary mb-4">{{ reward.description }}</p>
              <div class="d-flex justify-content-between align-items-center mt-auto">
                <span :class="`badge bg-${reward.color} bg-opacity-10 text-${reward.color} fs-6 px-3 py-2`">
                  {{ reward.points }} puntos
                </span>
                <div class="d-flex gap-2">
                  <button :class="`btn btn-outline-${reward.color} d-flex align-items-center hover-btn`">
                    Editar
                  </button>
                  <button :class="`btn btn-outline-${reward.color} d-flex align-items-center hover-btn`">
                    Eliminar
                  </button>
                </div>
              </div>
            </div>
          </div>
        </div>
      </div>

      <!-- Costo Medio -->
      <h5 class="fw-bold text-dark mb-3 d-flex align-items-center gap-2">
        <i class="bi bi-stars text-danger"></i>
        <span>Costo Medio</span>
      </h5>
      <div class="row g-4">
        <div class="col-md-4" v-for="reward in midCostRewards" :key="reward.title">
          <div class="card h-100 border-0 shadow-sm hover-card">
            <div class="card-body d-flex flex-column p-4">
              <div class="d-flex align-items-center mb-3">
                <div
                  :class="`bg-${reward.color} bg-opacity-10 d-flex align-items-center justify-content-center rounded-circle me-3`"
                  style="width: 48px; height: 48px;">
                  <i :class="`bi bi-${reward.icon} text-${reward.color}`" style="font-size: 1.5rem;"></i>
                </div>
                <h5 class="card-title mb-0 text-dark">{{ reward.title }}</h5>
              </div>
              <p class="card-text text-secondary mb-4">{{ reward.description }}</p>
              <div class="d-flex justify-content-between align-items-center mt-auto">
                <span :class="`badge bg-${reward.color} bg-opacity-10 text-${reward.color} fs-6 px-3 py-2`">
                  {{ reward.points }} puntos
                </span>
                <div class="d-flex gap-2">
                  <button :class="`btn btn-outline-${reward.color} d-flex align-items-center hover-btn`">
                    Editar
                  </button>
                  <button :class="`btn btn-outline-${reward.color} d-flex align-items-center hover-btn`">
                    Eliminar
                  </button>
                </div>
              </div>
            </div>
          </div>
        </div>
      </div>
    </div>
  </div>
</template>

<style scoped>
/* Clases adicionales para Bootstrap */
.bg-purple {
  background-color: #6e42c14c;
}

.text-purple {
  color: #6f42c1;
}

.btn-outline-purple {
  color: #6f42c1;
  border-color: #6f42c1;
}

.btn-outline-purple:hover {
  background-color: #6f42c1;
  color: white;
}

/* Animaciones y efectos hover */
.hover-card {
  transition: all 0.3s ease;
  transform: translateY(0);
}

.hover-card:hover {
  transform: translateY(-5px);
  box-shadow: 0 10px 20px rgba(0, 0, 0, 0.1) !important;
}

.hover-btn {
  transition: all 0.2s ease;
}

/* Efectos hover específicos para cada botón */
.btn-outline-warning:hover {
  background-color: #ffc107 !important;
  color: black !important;
}

.btn-outline-info:hover {
  background-color: #0dcaf0 !important;
  color: white !important;
}

.btn-outline-success:hover {
  background-color: #198754 !important;
  color: white !important;
}

.btn-outline-danger:hover {
  background-color: #dc3545 !important;
  color: white !important;
}

.btn-outline-primary:hover {
  background-color: #0d6efd !important;
  color: white !important;
}

/* Asegurar que los círculos sean perfectos */
.rounded-circle {
  aspect-ratio: 1/1;
  display: flex;
  align-items: center;
  justify-content: center;
}

/* Espaciado entre botones */
.gap-2 {
  gap: 0.5rem;
}

/* Estilos para el progreso */
.progress {
  height: 12px;
  border-radius: 6px;
  background-color: #f0f0f0;
}

.stat-label {
  font-size: 0.95rem;
  color: #6c757d;
}

.alert {
  border-radius: 10px;
  font-size: 0.9rem;
  padding: 12px 16px;
  border: 1px solid rgba(13, 110, 253, 0.2);
}

.list-group-item {
  padding: 12px 16px;
  border-bottom: 1px solid #f0f0f0;
}

.list-group-item:last-child {
  border-bottom: none;
}
</style>