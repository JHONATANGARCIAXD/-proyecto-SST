<template>
    <div class="pt-4 px-4">
        <!-- Encabezado -->
        <div class="col-12 d-flex justify-content-between align-items-center mb-4">
            <div>
                <h4 class="fw-bold mb-0">Gestión de Empleados</h4>
            </div>
            <div class="d-flex gap-3">
                <button class="btn btn-outline-secondary px-3 py-2 d-flex align-items-center gap-2">
                    <i class="bi bi-funnel"></i> Filtrar
                </button>
                <button class="btn btn-primary px-3 py-2 d-flex align-items-center gap-2" data-bs-toggle="modal"
                    data-bs-target="#exampleModal">
                    <i class="bi bi-plus-lg"></i> Agregar Empleado
                </button>
            </div>
        </div>

        <!-- Tabla de empleados -->
        <div class="col-12">
            <div class="card border-0 shadow-sm rounded-3 overflow-hidden">
                <div class="table-responsive">
                    <table class="table table-hover align-middle mb-0">
                        <thead class="table-light">
                            <tr>
                                <th class="ps-4">EMPLEADO</th>
                                <th>CARGO</th>
                                <th>DEPARTAMENTO</th>
                                <th>PUNTOS</th>
                                <th>NIVEL</th>
                                <th class="text-end pe-4">ACCIONES</th>
                            </tr>
                        </thead>
                        <tbody>
                            <tr v-for="empleado in empleados" :key="empleado.id">
                                <td class="ps-4">
                                    <div class="d-flex align-items-center gap-3">
                                        <div class="avatar bg-primary bg-opacity-10 text-primary d-flex align-items-center justify-content-center"
                                            style="width: 40px; height: 40px; font-weight: 600;">
                                            {{ empleado.iniciales }}
                                        </div>
                                        <div>
                                            <div class="fw-semibold">{{ empleado.nombre }}</div>
                                            <small class="text-muted">{{ empleado.email }}</small>
                                        </div>
                                    </div>
                                </td>
                                <td>{{ empleado.cargo }}</td>
                                <td>
                                    <span class="badge bg-light text-dark">{{ empleado.departamento }}</span>
                                </td>
                                <td>
                                    <div class="d-flex align-items-center gap-2">
                                        <i class="bi bi-star-fill text-warning"></i>
                                        <span class="fw-medium">{{ empleado.puntos }}</span>
                                    </div>
                                </td>
                                <td>
                                    <span :class="'badge rounded-pill py-2 px-3 nivel-' + empleado.nivel.toLowerCase()">
                                        {{ empleado.nivel }}
                                    </span>
                                </td>
                                <td class="text-end pe-4">
                                    <div class="d-flex gap-2 justify-content-end">
                                        <button class="btn btn-sm btn-outline-primary">
                                            <i class="bi bi-pencil"></i>
                                        </button>
                                        <button class="btn btn-sm btn-outline-danger">
                                            <i class="bi bi-trash"></i>
                                        </button>
                                    </div>
                                </td>
                            </tr>
                        </tbody>
                    </table>
                </div>
            </div>
        </div>

        <!-- Modal para agregar empleado -->
        <div class="modal fade" id="exampleModal" tabindex="-1" aria-labelledby="exampleModalLabel" aria-hidden="true">
            <!-- ... (mantener el mismo contenido del modal) ... -->
        </div>
    </div>
</template>

<script setup>
const empleados = [
    {
        id: 1,
        iniciales: 'AG',
        nombre: 'Ana García López',
        email: 'ana.garcia@empresa.com',
        cargo: 'Desarrolladora Senior',
        departamento: 'IT',
        puntos: 2850,
        nivel: 'Experto'
    },
    {
        id: 2,
        iniciales: 'CR',
        nombre: 'Carlos Rodríguez',
        email: 'carlos.rodriguez@empresa.com',
        cargo: 'Analista de Datos',
        departamento: 'Analytics',
        puntos: 2340,
        nivel: 'Avanzado'
    },
    {
        id: 3,
        iniciales: 'MF',
        nombre: 'María Fernández',
        email: 'maria.fernandez@empresa.com',
        cargo: 'Diseñadora UX',
        departamento: 'Diseño',
        puntos: 1890,
        nivel: 'Intermedio'
    }
]
</script>

<style scoped>
/* Estilos personalizados */
.avatar {
    border-radius: 50%;
    font-size: 0.9rem;
}

.table th {
    font-weight: 500;
    color: #6c757d;
    text-transform: uppercase;
    font-size: 0.75rem;
    letter-spacing: 0.5px;
}

.table-hover tbody tr:hover {
    background-color: rgba(13, 110, 253, 0.05);
}

/* Estilos para los niveles */
.nivel-experto {
    background-color: #eae2f8;
    color: #6f42c1;
}

.nivel-avanzado {
    background-color: #dceeff;
    color: #0d6efd;
}

.nivel-intermedio {
    background-color: #d6f5e3;
    color: #198754;
}
</style>