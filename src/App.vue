<script setup>
import { ref } from 'vue';
import Dashboard from './components/Dashboard.vue';
import DashboardView from './components/DashboardView.vue';
import Empleados from './components/Empleados.vue';
import Recompensas from './components/Recompensas.vue';
import RecompensasView from './components/RecompensasView.vue';
import SaludView from './components/SaludView.vue';
import RecomendacionesView from './components/RecomendacionesView.vue';
import ActividadView from './components/ActividadView.vue';

// Estados para controlar la autenticación y el rol
const isAuthenticated = ref(false);
const userRole = ref('');
const activeTab = ref('dashboard');

// Roles y sus permisos con componentes específicos
const roles = {
  admin: {
    name: 'Administrador',
    tabs: [
      { id: 'dashboard', name: 'Dashboard', icon: 'bi-house', component: Dashboard },
      { id: 'empleados', name: 'Empleados', icon: 'bi-people', component: Empleados },
      { id: 'recompensas', name: 'Recompensas', icon: 'bi-gift', component: Recompensas }
    ]
  },
  employee: {
    name: 'Empleado',
    tabs: [
      { id: 'dashboardview', name: 'Dashboard', icon: 'bi-house', component: DashboardView },
      { id: 'recompensasview', name: 'Recompensas', icon: 'bi-gift', component: RecompensasView },
      { id: 'salud', name: 'Salud', icon: 'bi-heart-pulse', component: SaludView },
      { id: 'recomendaciones', name: 'Recomendaciones', icon: 'bi-lightbulb', component: RecomendacionesView },
      { id: 'actividad', name: 'Actividad', icon: 'bi-activity', component: ActividadView }
    ]
  }
};

// Función para obtener iniciales del usuario
const getUserInitials = () => {
  const name = "Usuario Actual";
  return name.split(' ').map(n => n[0]).join('').toUpperCase();
};

// Función para iniciar sesión (simulada)
const login = () => {
  isAuthenticated.value = true;
  activeTab.value = roles[userRole.value].tabs[0].id;
};

// Función para cerrar sesión
const logout = () => {
  isAuthenticated.value = false;
  userRole.value = '';
  activeTab.value = 'dashboard';
};

// Obtener el componente activo basado en el rol y la pestaña seleccionada
const getActiveComponent = () => {
  const roleTabs = roles[userRole.value].tabs;
  const activeTabData = roleTabs.find(tab => tab.id === activeTab.value);
  return activeTabData ? activeTabData.component : null;
};
</script>

<template>
  <div v-if="!isAuthenticated" class="login-container d-flex justify-content-center align-items-center min-vh-100">
    <div class="card p-4" style="width: 400px;">
      <div class="card-body text-center">
        <h2 class="mb-4">Inicio de sesión</h2>

        <div class="mb-3">
          <label for="roleSelect" class="form-label">Selecciona tu rol:</label>
          <select id="roleSelect" class="form-select" v-model="userRole">
            <option value="" disabled>Selecciona un rol</option>
            <option value="admin">Administrador</option>
            <option value="employee">Empleado</option>
          </select>
        </div>

        <button @click="login" class="btn btn-primary w-100" :disabled="!userRole">
          Ingresar
        </button>
      </div>
    </div>
  </div>

  <div v-else class="app-container">
    <!-- Sidebar Navigation -->
    <div class="sidebar">
      <div class="sidebar-content">
        <!-- Header with Logo and Logout -->
        <div class="sidebar-header">
          <div class="d-flex justify-content-between align-items-center">
            <div class="d-flex align-items-center">
              <i class="bi bi-trophy me-2" style="font-size: 1.5rem; color: #4eacfd;"></i>
              <h3 class="mb-0 text-white">HR Gamification</h3>
            </div>
            <button @click="logout" class="btn btn-sm btn-outline-light logout-btn">
              <i class="bi bi-box-arrow-right"></i>
            </button>
          </div>
          
          <!-- User Role Badge -->
          <div class="user-role mt-3">
            <span class="text-muted small">Rol:</span>
            <span class="badge role-badge">{{ roles[userRole].name }}</span>
          </div>
        </div>

        <!-- Navigation Menu -->
        <nav class="sidebar-menu">
          <ul class="nav flex-column">
            <li class="nav-item" v-for="tab in roles[userRole].tabs" :key="tab.id">
              <button 
                @click="activeTab = tab.id"
                :class="['nav-link', activeTab === tab.id ? 'active' : '']"
              >
                <i :class="['bi', tab.icon, 'me-2']"></i>
                {{ tab.name }}
                <i class="bi bi-chevron-right arrow-icon"></i>
              </button>
            </li>
          </ul>
        </nav>

        <!-- Sidebar Footer -->
        <div class="sidebar-footer mt-auto">
          <div class="user-profile d-flex align-items-center">
            <div class="avatar bg-primary bg-opacity-10 text-primary">
              {{ getUserInitials() }}
            </div>
            <div class="user-info ms-2">
              <div class="user-name text-white small">Usuario Actual</div>
              <div class="user-email text-muted small">user@empresa.com</div>
            </div>
          </div>
        </div>
      </div>
    </div>

    <!-- Main Content -->
    <div class="main-content">
      <component :is="getActiveComponent()" />
    </div>
  </div>
</template>

<style scoped>
/* Sidebar Styles */
.sidebar {
  width: 250px;
  background: linear-gradient(180deg, #1a1a2e 0%, #16213e 100%);
  color: white;
  height: 100vh;
  position: fixed;
  box-shadow: 4px 0 15px rgba(0, 0, 0, 0.1);
  z-index: 1000;
}

.sidebar-content {
  display: flex;
  flex-direction: column;
  height: 100%;
  padding: 1.5rem 1rem;
}

.sidebar-header {
  padding-bottom: 1.5rem;
  border-bottom: 1px solid rgba(255, 255, 255, 0.1);
}

.logout-btn {
  border-radius: 50%;
  width: 32px;
  height: 32px;
  display: flex;
  align-items: center;
  justify-content: center;
}

.role-badge {
  background-color: rgba(78, 172, 253, 0.2);
  color: #4eacfd;
  font-weight: 500;
  padding: 0.35rem 0.75rem;
  border-radius: 50px;
  margin-left: 0.5rem;
}

.sidebar-menu {
  margin-top: 1.5rem;
  flex-grow: 1;
}

.nav-item {
  margin-bottom: 0.5rem;
}

.nav-link {
  width: 100%;
  text-align: left;
  color: rgba(255, 255, 255, 0.7);
  padding: 0.75rem 1rem;
  border-radius: 8px;
  display: flex;
  align-items: center;
  justify-content: space-between;
  background: transparent;
  border: none;
  transition: all 0.3s ease;
}

.nav-link:hover {
  background-color: rgba(255, 255, 255, 0.05);
  color: white;
}

.nav-link.active {
  background-color: rgba(78, 172, 253, 0.2);
  color: white;
  font-weight: 500;
}

.nav-link.active .arrow-icon {
  transform: translateX(3px);
}

.arrow-icon {
  font-size: 0.8rem;
  transition: transform 0.2s ease;
}

.sidebar-footer {
  padding-top: 1.5rem;
  border-top: 1px solid rgba(255, 255, 255, 0.1);
}

.avatar {
  width: 40px;
  height: 40px;
  border-radius: 50%;
  display: flex;
  align-items: center;
  justify-content: center;
  font-weight: 600;
}

.user-name {
  font-weight: 500;
}

.user-email {
  font-size: 0.75rem;
}

/* Main Content */
.app-container {
  display: flex;
  min-height: 100vh;
}

.main-content {
  flex: 1;
  margin-left: 250px;
  padding: 2rem;
  background-color: #f8f9fa;
}

/* Login Container */
.login-container {
  background-color: #f8f9fa;
}

/* Global Styles */
.stat-number {
  font-size: 2rem;
  font-weight: bold;
}

.stat-label {
  font-size: 0.9rem;
  color: #6c757d;
}

.card {
  border-radius: 12px;
  box-shadow: 0 4px 12px rgba(0, 0, 0, 0.05);
  margin-bottom: 20px;
  border: none;
  transition: transform 0.3s ease, box-shadow 0.3s ease;
}

.card:hover {
  transform: translateY(-2px);
  box-shadow: 0 6px 16px rgba(0, 0, 0, 0.1);
}

.card-header {
  background-color: #ffffff;
  border-bottom: 1px solid rgba(0, 0, 0, 0.1);
  font-weight: 600;
  border-radius: 12px 12px 0 0 !important;
}

.progress {
  height: 10px;
  border-radius: 5px;
}

/* Responsive */
@media (max-width: 992px) {
  .sidebar {
    width: 220px;
  }
  
  .main-content {
    margin-left: 220px;
  }
}

@media (max-width: 768px) {
  .sidebar {
    transform: translateX(-100%);
    transition: transform 0.3s ease;
  }
  
  .sidebar.open {
    transform: translateX(0);
  }
  
  .main-content {
    margin-left: 0;
  }
}
</style>