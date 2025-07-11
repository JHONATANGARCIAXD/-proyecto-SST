<template>
    <div class="bg-white min-vh-100 p-4">
        <!-- Título principal -->
        <h1 class="text-center mb-4 text-primary fw-bold">Recompensas Individuales</h1>

        <!-- Sección Bajo Costo -->
        <div class="mb-5">
            <h2 class="mb-3 d-flex align-items-center gap-2">
                <i class="bi bi-cup-hot text-warning"></i>
                <span class="text-dark">Bajo Costo</span>
            </h2>

            <div class="row g-4">
                <!-- Café Gratis -->
                <div class="col-md-4">
                    <div class="card h-100 border-0 shadow-sm hover-card">
                        <div class="card-body d-flex flex-column p-4">
                            <div class="d-flex align-items-center mb-3">
                                <div class="bg-warning bg-opacity-10 d-flex align-items-center justify-content-center rounded-circle me-3"
                                    style="width: 48px; height: 48px;">
                                    <i class="bi bi-cup-fill text-warning fs-4"></i>
                                </div>
                                <h5 class="card-title mb-0 text-dark">Café Gratis</h5>
                            </div>
                            <p class="card-text text-secondary mb-4">Disfruta de tu bebida favorita</p>
                            <div class="d-flex justify-content-between align-items-center mt-auto">
                                <span class="badge bg-warning bg-opacity-10 text-warning fs-6 px-3 py-2">50
                                    puntos</span>
                                <div class="d-flex gap-2">
                                    <button class="btn btn-outline-warning d-flex align-items-center hover-btn">
                                        Editar
                                    </button>
                                    <button class="btn btn-outline-warning d-flex align-items-center hover-btn">
                                        Eliminar
                                    </button>
                                </div>
                            </div>
                        </div>
                    </div>
                </div>

                <!-- Acceso Prioritario -->
                <div class="col-md-4">
                    <div class="card h-100 border-0 shadow-sm hover-card">
                        <div class="card-body d-flex flex-column p-4">
                            <div class="d-flex align-items-center mb-3">
                                <div class="bg-info bg-opacity-10 d-flex align-items-center justify-content-center rounded-circle me-3"
                                    style="width: 48px; height: 48px;">
                                    <i class="bi bi-clock-fill text-info fs-4"></i>
                                </div>
                                <h5 class="card-title mb-0 text-dark">Acceso Prioritario</h5>
                            </div>
                            <p class="card-text text-secondary mb-4">Evita las filas en hora pico</p>
                            <div class="d-flex justify-content-between align-items-center mt-auto">
                                <span class="badge bg-info bg-opacity-10 text-info fs-6 px-3 py-2">100 puntos</span>
                                <div class="d-flex gap-2">
                                    <button class="btn btn-outline-info d-flex align-items-center hover-btn">
                                        Editar
                                    </button>
                                    <button class="btn btn-outline-info d-flex align-items-center hover-btn">
                                        Eliminar
                                    </button>
                                </div>
                            </div>
                        </div>
                    </div>
                </div>

                <!-- Reconocimiento Digital -->
                <div class="col-md-4">
                    <div class="card h-100 border-0 shadow-sm hover-card">
                        <div class="card-body d-flex flex-column p-4">
                            <div class="d-flex align-items-center mb-3">
                                <div class="bg-success bg-opacity-10 d-flex align-items-center justify-content-center rounded-circle me-3"
                                    style="width: 48px; height: 48px;">
                                    <i class="bi bi-trophy-fill text-success fs-4"></i>
                                </div>
                                <h5 class="card-title mb-0 text-dark">Reconocimiento Digital</h5>
                            </div>
                            <p class="card-text text-secondary mb-4">Aparece en el muro interno</p>
                            <div class="d-flex justify-content-between align-items-center mt-auto">
                                <span class="badge bg-success bg-opacity-10 text-success fs-6 px-3 py-2">75
                                    puntos</span>
                                <div class="d-flex gap-2">
                                    <button class="btn btn-outline-success d-flex align-items-center hover-btn">
                                        Editar
                                    </button>
                                    <button class="btn btn-outline-success d-flex align-items-center hover-btn">
                                        Eliminar
                                    </button>
                                </div>
                            </div>
                        </div>
                    </div>
                </div>
            </div>
        </div>

        <!-- Sección Costo Medio -->
        <div class="mb-5">
            <h2 class="mb-3 d-flex align-items-center gap-2">
                <i class="bi bi-stars text-danger"></i>
                <span class="text-dark">Costo Medio</span>
            </h2>

            <div class="row g-4">
                <!-- Medio Día Libre -->
                <div class="col-md-4">
                    <div class="card h-100 border-0 shadow-sm hover-card">
                        <div class="card-body d-flex flex-column p-4">
                            <div class="d-flex align-items-center mb-3">
                                <div class="bg-danger bg-opacity-10 d-flex align-items-center justify-content-center rounded-circle me-3"
                                    style="width: 48px; height: 48px;">
                                    <i class="bi bi-sun-fill text-danger fs-4"></i>
                                </div>
                                <h5 class="card-title mb-0 text-dark">Medio Día Libre</h5>
                            </div>
                            <p class="card-text text-secondary mb-4">Descansa y disfruta tu tiempo</p>
                            <div class="d-flex justify-content-between align-items-center mt-auto">
                                <span class="badge bg-danger bg-opacity-10 text-danger fs-6 px-3 py-2">500 puntos</span>
                                <div class="d-flex gap-2">
                                    <button class="btn btn-outline-danger d-flex align-items-center hover-btn">
                                        Editar
                                    </button>
                                    <button class="btn btn-outline-danger d-flex align-items-center hover-btn">
                                        Eliminar
                                    </button>
                                </div>
                            </div>
                        </div>
                    </div>
                </div>

                <!-- Bono Apps Comida -->
                <div class="col-md-4">
                    <div class="card h-100 border-0 shadow-sm hover-card">
                        <div class="card-body d-flex flex-column p-4">
                            <div class="d-flex align-items-center mb-3">
                                <div class="bg-primary bg-opacity-10 d-flex align-items-center justify-content-center rounded-circle me-3"
                                    style="width: 48px; height: 48px;">
                                    <i class="bi bi-egg-fried text-primary fs-4"></i>
                                </div>
                                <h5 class="card-title mb-0 text-dark">Bono Apps Comida</h5>
                            </div>
                            <p class="card-text text-secondary mb-4">$20 USD para delivery</p>
                            <div class="d-flex justify-content-between align-items-center mt-auto">
                                <span class="badge bg-primary bg-opacity-10 text-primary fs-6 px-3 py-2">400
                                    puntos</span>
                                <div class="d-flex gap-2">
                                    <button class="btn btn-outline-primary d-flex align-items-center hover-btn">
                                        Editar
                                    </button>
                                    <button class="btn btn-outline-primary d-flex align-items-center hover-btn">
                                        Eliminar
                                    </button>
                                </div>
                            </div>
                        </div>
                    </div>
                </div>

                <!-- Entrada a Rifa -->
                <div class="col-md-4">
                    <div class="card h-100 border-0 shadow-sm hover-card">
                        <div class="card-body d-flex flex-column p-4">
                            <div class="d-flex align-items-center mb-3">
                                <div class="bg-purple bg-opacity-10 d-flex align-items-center justify-content-center rounded-circle me-3"
                                    style="width: 48px; height: 48px;">
                                    <i class="bi bi-gift-fill text-purple fs-4"></i>
                                </div>
                                <h5 class="card-title mb-0 text-dark">Entrada a Rifa</h5>
                            </div>
                            <p class="card-text text-secondary mb-4">Participa por premios increíbles</p>
                            <div class="d-flex justify-content-between align-items-center mt-auto">
                                <span class="badge bg-purple bg-opacity-10 text-purple fs-6 px-3 py-2">300 puntos</span>
                                <div class="d-flex gap-2">
                                    <button class="btn btn-outline-purple d-flex align-items-center hover-btn">
                                        Editar
                                    </button>
                                    <button class="btn btn-outline-purple d-flex align-items-center hover-btn">
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

    <!-- Recompensas Grupales -->
    <div class="bg-white min-vh-100 p-4">
        <h1 class="text-center mb-4 text-primary fw-bold">Recompensas Grupales</h1>

        <!-- Sección Bajo Costo -->
        <div class="mb-5">
            <h2 class="mb-3 d-flex align-items-center gap-2">
                <i class="bi bi-people-fill text-warning"></i>
                <span class="text-dark">Bajo Costo</span>
            </h2>

            <div class="row g-4">
                <!-- Almuerzo de Equipo -->
                <div class="col-md-4">
                    <div class="card h-100 border-0 shadow-sm hover-card">
                        <div class="card-body d-flex flex-column p-4">
                            <div class="d-flex align-items-center mb-3">
                                <div class="bg-warning bg-opacity-10 d-flex align-items-center justify-content-center rounded-circle me-3"
                                    style="width: 48px; height: 48px;">
                                    <i class="bi bi-egg-fried text-warning fs-4"></i>
                                </div>
                                <h5 class="card-title mb-0 text-dark">Almuerzo de Equipo</h5>
                            </div>
                            <p class="card-text text-secondary mb-4">Comida grupal para 5 personas</p>
                            <div class="d-flex justify-content-between align-items-center mt-auto">
                                <span class="badge bg-warning bg-opacity-10 text-warning fs-6 px-3 py-2">800
                                    puntos</span>
                                <div class="d-flex gap-2">
                                    <button class="btn btn-outline-warning d-flex align-items-center hover-btn">
                                        Editar
                                    </button>
                                    <button class="btn btn-outline-warning d-flex align-items-center hover-btn">
                                        Eliminar
                                    </button>
                                </div>
                            </div>
                        </div>
                    </div>
                </div>

                <!-- Día de Home Office -->
                <div class="col-md-4">
                    <div class="card h-100 border-0 shadow-sm hover-card">
                        <div class="card-body d-flex flex-column p-4">
                            <div class="d-flex align-items-center mb-3">
                                <div class="bg-info bg-opacity-10 d-flex align-items-center justify-content-center rounded-circle me-3"
                                    style="width: 48px; height: 48px;">
                                    <i class="bi bi-house-door-fill text-info fs-4"></i>
                                </div>
                                <h5 class="card-title mb-0 text-dark">Día de Home Office</h5>
                            </div>
                            <p class="card-text text-secondary mb-4">Trabajo remoto para todo el equipo</p>
                            <div class="d-flex justify-content-between align-items-center mt-auto">
                                <span class="badge bg-info bg-opacity-10 text-info fs-6 px-3 py-2">600 puntos</span>
                                <div class="d-flex gap-2">
                                    <button class="btn btn-outline-info d-flex align-items-center hover-btn">
                                        Editar
                                    </button>
                                    <button class="btn btn-outline-info d-flex align-items-center hover-btn">
                                        Eliminar
                                    </button>
                                </div>
                            </div>
                        </div>
                    </div>
                </div>

                <!-- Taller Especializado -->
                <div class="col-md-4">
                    <div class="card h-100 border-0 shadow-sm hover-card">
                        <div class="card-body d-flex flex-column p-4">
                            <div class="d-flex align-items-center mb-3">
                                <div class="bg-success bg-opacity-10 d-flex align-items-center justify-content-center rounded-circle me-3"
                                    style="width: 48px; height: 48px;">
                                    <i class="bi bi-book-fill text-success fs-4"></i>
                                </div>
                                <h5 class="card-title mb-0 text-dark">Taller Especializado</h5>
                            </div>
                            <p class="card-text text-secondary mb-4">Capacitación para tu equipo</p>
                            <div class="d-flex justify-content-between align-items-center mt-auto">
                                <span class="badge bg-success bg-opacity-10 text-success fs-6 px-3 py-2">750
                                    puntos</span>
                                <div class="d-flex gap-2">
                                    <button class="btn btn-outline-success d-flex align-items-center hover-btn">
                                        Editar
                                    </button>
                                    <button class="btn btn-outline-success d-flex align-items-center hover-btn">
                                        Eliminar
                                    </button>
                                </div>
                            </div>
                        </div>
                    </div>
                </div>
            </div>
        </div>

        <!-- Sección Costo Medio -->
        <div class="mb-5">
            <h2 class="mb-3 d-flex align-items-center gap-2">
                <i class="bi bi-award-fill text-danger"></i>
                <span class="text-dark">Costo Medio</span>
            </h2>

            <div class="row g-4">
                <!-- Salida Grupal -->
                <div class="col-md-4">
                    <div class="card h-100 border-0 shadow-sm hover-card">
                        <div class="card-body d-flex flex-column p-4">
                            <div class="d-flex align-items-center mb-3">
                                <div class="bg-danger bg-opacity-10 d-flex align-items-center justify-content-center rounded-circle me-3"
                                    style="width: 48px; height: 48px;">
                                    <i class="bi bi-emoji-sunglasses-fill text-danger fs-4"></i>
                                </div>
                                <h5 class="card-title mb-0 text-dark">Salida Grupal</h5>
                            </div>
                            <p class="card-text text-secondary mb-4">Actividad recreativa para el equipo</p>
                            <div class="d-flex justify-content-between align-items-center mt-auto">
                                <span class="badge bg-danger bg-opacity-10 text-danger fs-6 px-3 py-2">1,200
                                    puntos</span>
                                <div class="d-flex gap-2">
                                    <button class="btn btn-outline-danger d-flex align-items-center hover-btn">
                                        Editar
                                    </button>
                                    <button class="btn btn-outline-danger d-flex align-items-center hover-btn">
                                        Eliminar
                                    </button>
                                </div>
                            </div>
                        </div>
                    </div>
                </div>

                <!-- Bonificación Grupal -->
                <div class="col-md-4">
                    <div class="card h-100 border-0 shadow-sm hover-card">
                        <div class="card-body d-flex flex-column p-4">
                            <div class="d-flex align-items-center mb-3">
                                <div class="bg-primary bg-opacity-10 d-flex align-items-center justify-content-center rounded-circle me-3"
                                    style="width: 48px; height: 48px;">
                                    <i class="bi bi-cash-stack text-primary fs-4"></i>
                                </div>
                                <h5 class="card-title mb-0 text-dark">Bonificación Grupal</h5>
                            </div>
                            <p class="card-text text-secondary mb-4">$100 USD por miembro</p>
                            <div class="d-flex justify-content-between align-items-center mt-auto">
                                <span class="badge bg-primary bg-opacity-10 text-primary fs-6 px-3 py-2">2,000
                                    puntos</span>
                                <div class="d-flex gap-2">
                                    <button class="btn btn-outline-primary d-flex align-items-center hover-btn">
                                        Editar
                                    </button>
                                    <button class="btn btn-outline-primary d-flex align-items-center hover-btn">
                                        Eliminar
                                    </button>
                                </div>
                            </div>
                        </div>
                    </div>
                </div>

                <!-- Viaje de Trabajo -->
                <div class="col-md-4">
                    <div class="card h-100 border-0 shadow-sm hover-card">
                        <div class="card-body d-flex flex-column p-4">
                            <div class="d-flex align-items-center mb-3">
                                <div class="bg-purple bg-opacity-10 d-flex align-items-center justify-content-center rounded-circle me-3"
                                    style="width: 48px; height: 48px;">
                                    <i class="bi bi-airplane-fill text-purple fs-4"></i>
                                </div>
                                <h5 class="card-title mb-0 text-dark">Viaje de Trabajo</h5>
                            </div>
                            <p class="card-text text-secondary mb-4">Retiro grupal por 3 días</p>
                            <div class="d-flex justify-content-between align-items-center mt-auto">
                                <span class="badge bg-purple bg-opacity-10 text-purple fs-6 px-3 py-2">3,500
                                    puntos</span>
                                <div class="d-flex gap-2">
                                    <button class="btn btn-outline-purple d-flex align-items-center hover-btn">
                                        Editar
                                    </button>
                                    <button class="btn btn-outline-purple d-flex align-items-center hover-btn">
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

<style>
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
</style>