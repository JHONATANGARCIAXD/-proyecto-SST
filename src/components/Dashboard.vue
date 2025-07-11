<template>
  <div class="text-white min-vh-100 px-4">
    <!-- Tarjetas superiores (Métricas clave) -->
    <div class="d-flex flex-wrap py-5 gap-3">
      <!-- Tarjeta 1 - Empleados -->
      <div
        class="card text-white bg-primary bg-gradient d-flex flex-row align-items-center justify-content-between p-3 rounded-4"
        style="width: 250px;">
        <div>
          <div style="font-size: 0.8rem;">Total Empleados</div>
          <div style="font-size: 1.5rem; font-weight: bold;">{{ totalEmpleados }}</div>
          <div style="font-size: 0.7rem;">+5% este mes</div>
        </div>
        <div>
          <i class="bi bi-people" style="font-size: 1.8rem;"></i>
        </div>
      </div>

      <!-- Tarjeta 2 - Actividad -->
      <div
        class="card text-white bg-success bg-gradient d-flex flex-row align-items-center justify-content-between p-3 rounded-4"
        style="width: 250px;">
        <div>
          <div style="font-size: 0.8rem;">Actividad Hoy</div>
          <div style="font-size: 1.5rem; font-weight: bold;">{{ actividadesHoy }}</div>
          <div style="font-size: 0.7rem;">Canjes: {{ canjesHoy }}</div>
        </div>
        <div>
          <i class="bi bi-activity" style="font-size: 1.8rem;"></i>
        </div>
      </div>

      <!-- Tarjeta 3 - Wearables -->
      <div
        class="card text-white bg-danger bg-gradient d-flex flex-row align-items-center justify-content-between p-3 rounded-4"
        style="width: 250px;">
        <div>
          <div style="font-size: 0.8rem;">Wearables Activos</div>
          <div style="font-size: 1.5rem; font-weight: bold;">{{ wearablesActivos }}</div>
          <div style="font-size: 0.7rem;">De {{ totalWearables }} total</div>
        </div>
        <div>
          <i class="bi bi-watch" style="font-size: 1.8rem;"></i>
        </div>
      </div>

      <!-- Tarjeta 4 - Puntos -->
      <div
        class="card text-dark text-white bg-amber bg-gradient d-flex flex-row align-items-center justify-content-between p-3 rounded-4"
        style="width: 250px;">
        <div>
          <div style="font-size: 0.8rem;">Puntos Otorgados</div>
          <div style="font-size: 1.5rem; font-weight: bold;">{{ puntosTotales }}</div>
        </div>
        <div>
          <i class="bi bi-star-fill" style="font-size: 1.8rem;"></i>
        </div>
      </div>
    </div>

    <!-- Sección doble: Mejores empleados + Equipos -->
    <div class="d-flex gap-4 mb-4">
      <!-- Mejores Empleados -->
      <div class="card p-4 rounded-4 flex-grow-1">
        <div class="d-flex justify-content-between align-items-center mb-4">
          <h5 class="mb-0">Top Empleados</h5>
          <router-link to="/empleados" class="btn btn-sm btn-outline-light">
            Ver todos
          </router-link>
        </div>

        <div v-for="empleado in topEmpleados" :key="empleado.nombre"
          class="d-flex align-items-center justify-content-between bg-light rounded-3 p-3 mb-3 text-dark">
          <div class="d-flex align-items-center gap-3">
            <div class="rounded-circle bg-primary text-white d-flex align-items-center justify-content-center"
              style="width: 45px; height: 45px; font-weight: bold;">
              {{ empleado.iniciales }}
            </div>
            <div>
              <div class="fw-semibold">{{ empleado.nombre }}</div>
              <div class="text-muted small">{{ empleado.departamento }}</div>
            </div>
          </div>
          <div class="text-end d-flex gap-1">
            <i class="bi bi-star-fill text-warning"></i>
            <span class="fw-semibold">{{ empleado.puntos }}</span>
          </div>
        </div>
      </div>

      <!-- Mejores Equipos -->
      <div class="card p-4 rounded-4 flex-grow-1">
        <div class="d-flex justify-content-between align-items-center mb-4">
          <h5 class="mb-0">Ranking de Equipos</h5>
          <router-link to="/equipos" class="btn btn-sm btn-outline-light">
            Ver todos
          </router-link>
        </div>

        <div v-for="(equipo, index) in topEquipos" :key="equipo.nombre"
          class="d-flex align-items-center justify-content-between bg-light rounded-3 p-3 mb-3 text-dark">
          <div class="d-flex align-items-center gap-3">
            <div class="rounded-circle text-white d-flex align-items-center justify-content-center"
              :class="'bg-' + coloresRanking[index]" style="width: 45px; height: 45px; font-weight: bold;">
              {{ index + 1 }}
            </div>
            <div>
              <div class="fw-semibold">{{ equipo.nombre }}</div>
              <div class="text-muted small">Líder: {{ equipo.lider }}</div>
            </div>
          </div>
          <div class="text-end d-flex gap-1">
            <i class="bi bi-trophy-fill text-warning"></i>
            <span class="fw-semibold">{{ equipo.puntos }} pts</span>
          </div>
        </div>
      </div>
    </div>


    <!-- Últimas actividades -->
    <div class="card p-4 rounded-4 mb-4">
      <div class="d-flex justify-content-between align-items-center mb-4">
        <h5 class="mb-0">Registro de Actividades</h5>
        <button class="btn btn-sm btn-outline-light" @click="actualizarActividades">
          <i class="bi bi-arrow-clockwise"></i> Actualizar
        </button>
      </div>
      <table class="table table-light table-hover">
        <thead>
          <tr>
            <th>Fecha</th>
            <th>Empleado</th>
            <th>Acción</th>
            <th>Detalle</th>
            <th>Puntos</th>
          </tr>
        </thead>
        <tbody>
          <tr v-for="actividad in actividadesRecientes" :key="actividad.id">
            <td>{{ actividad.fecha }}</td>
            <td>{{ actividad.empleado }}</td>
            <td>
              <span :class="'badge bg-' + actividad.color">
                {{ actividad.accion }}
              </span>
            </td>
            <td>{{ actividad.detalle }}</td>
            <td>{{ actividad.puntos || '-' }}</td>
          </tr>
        </tbody>
      </table>
    </div>
  </div>
</template>

<script>
export default {
  data() {
    return {
      showNotificationModal: false,
      totalEmpleados: 42,
      actividadesHoy: 28,
      canjesHoy: 7,
      wearablesActivos: 42,
      totalWearables: 45,
      puntosTotales: '15,280',
      puntosPromedio: '364',
      coloresRanking: ['gold', 'silver', 'bronze', 'secondary', 'secondary'],
      topEmpleados: [
        { iniciales: 'AG', nombre: 'Ana García', departamento: 'Desarrollo', puntos: 2850 },
        { iniciales: 'CR', nombre: 'Carlos Rodríguez', departamento: 'Datos', puntos: 2340 },
        { iniciales: 'MF', nombre: 'María Fernández', departamento: 'Diseño', puntos: 1890 },
        { iniciales: 'JP', nombre: 'Juan Pérez', departamento: 'Marketing', puntos: 1750 },
        { iniciales: 'LM', nombre: 'Laura Martínez', departamento: 'Ventas', puntos: 1620 }
      ],
      topEquipos: [
        { nombre: 'Equipo Backend', lider: 'Ana García', puntos: 7400 },
        { nombre: 'Equipo Frontend', lider: 'Carlos R.', puntos: 6300 },
        { nombre: 'Equipo Datos', lider: 'María F.', puntos: 5800 },
        { nombre: 'Equipo UX', lider: 'Juan P.', puntos: 5200 },
        { nombre: 'Equipo Mobile', lider: 'Laura M.', puntos: 4850 }
      ],
      solicitudesPendientes: [
        { iniciales: 'TG', nombre: 'Tomás González', recompensa: 'Día libre' },
        { iniciales: 'SR', nombre: 'Sofía Ramírez', recompensa: 'Bono comida' },
        { iniciales: 'DP', nombre: 'David Pérez', recompensa: 'Curso premium' },
        { iniciales: 'LC', nombre: 'Lucía Castro', recompensa: 'Home office' }
      ],
      actividadesRecientes: [
        { id: 1, fecha: '15/11 09:30', empleado: 'Ana García', accion: 'Canje', color: 'success', detalle: 'Café gratis', puntos: -50 },
        { id: 2, fecha: '15/11 10:15', empleado: 'Carlos R.', accion: 'Logro', color: 'info', detalle: 'Proyecto completado', puntos: +200 },
        { id: 3, fecha: '14/11 16:45', empleado: 'María F.', accion: 'Canje', color: 'success', detalle: 'Día libre', puntos: -500 },
        { id: 5, fecha: '14/11 11:05', empleado: 'Juan P.', accion: 'Reconocimiento', color: 'primary', detalle: 'Empleado del mes', puntos: +300 }
      ]
    }
  },
  methods: {
    navigateTo(route) {
      this.$router.push(route);
    },
    actualizarActividades() {
      // Lógica para actualizar actividades
      console.log("Actualizando actividades...");
    }
  }
}
</script>

<style scoped>
/* Colores personalizados */
.bg-gold {
  background-color: #FFD700 !important;
}

.bg-silver {
  background-color: #C0C0C0 !important;
}

.bg-bronze {
  background-color: #CD7F32 !important;
}

.bg-amber {
  background-color: #ffa000;
  background-image: linear-gradient(135deg, #ffa000 0%, #ffca28 100%);
}

/* Efectos hover */
.hover-action-card {
  transition: all 0.2s ease;
  cursor: pointer;
  border: 1px solid transparent;
}

.hover-action-card:hover {
  transform: translateY(-3px);
  border-color: var(--bs-primary) !important;
  box-shadow: 0 5px 15px rgba(0, 0, 0, 0.3);
}

/* Estilos de tabla */

.table th {
  border-bottom: 1px solid #495057;
  font-weight: 500;
}

.table td {
  border-bottom: 1px solid #343a40;
  vertical-align: middle;
}

</style>