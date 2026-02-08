<template>
  <div class="carta-container">
    <!-- Decoración izquierda -->
    <div class="decoracion decoracion-izquierda">
      <div class="linea-decorativa linea-1"></div>
      <div class="linea-decorativa linea-2"></div>
      <div class="elemento-floral floral-1">
        <svg viewBox="0 0 100 100" xmlns="http://www.w3.org/2000/svg">
          <circle cx="50" cy="50" r="8" fill="#ff8fab" opacity="0.6"/>
          <circle cx="50" cy="30" r="6" fill="#ffaec9" opacity="0.5"/>
          <circle cx="70" cy="50" r="6" fill="#ffaec9" opacity="0.5"/>
          <circle cx="50" cy="70" r="6" fill="#ffaec9" opacity="0.5"/>
          <circle cx="30" cy="50" r="6" fill="#ffaec9" opacity="0.5"/>
        </svg>
      </div>
      <div class="elemento-floral floral-2">
        <svg viewBox="0 0 100 100" xmlns="http://www.w3.org/2000/svg">
          <circle cx="50" cy="50" r="8" fill="#ff8fab" opacity="0.6"/>
          <circle cx="50" cy="30" r="6" fill="#ffaec9" opacity="0.5"/>
          <circle cx="70" cy="50" r="6" fill="#ffaec9" opacity="0.5"/>
          <circle cx="50" cy="70" r="6" fill="#ffaec9" opacity="0.5"/>
          <circle cx="30" cy="50" r="6" fill="#ffaec9" opacity="0.5"/>
        </svg>
      </div>
      <div class="detalle-elegante detalle-1"></div>
      <div class="detalle-elegante detalle-2"></div>
    </div>

    <!-- Decoración derecha -->
    <div class="decoracion decoracion-derecha">
      <div class="linea-decorativa linea-1"></div>
      <div class="linea-decorativa linea-2"></div>
      <div class="elemento-floral floral-1">
        <svg viewBox="0 0 100 100" xmlns="http://www.w3.org/2000/svg">
          <circle cx="50" cy="50" r="8" fill="#ff8fab" opacity="0.6"/>
          <circle cx="50" cy="30" r="6" fill="#ffaec9" opacity="0.5"/>
          <circle cx="70" cy="50" r="6" fill="#ffaec9" opacity="0.5"/>
          <circle cx="50" cy="70" r="6" fill="#ffaec9" opacity="0.5"/>
          <circle cx="30" cy="50" r="6" fill="#ffaec9" opacity="0.5"/>
        </svg>
      </div>
      <div class="elemento-floral floral-2">
        <svg viewBox="0 0 100 100" xmlns="http://www.w3.org/2000/svg">
          <circle cx="50" cy="50" r="8" fill="#ff8fab" opacity="0.6"/>
          <circle cx="50" cy="30" r="6" fill="#ffaec9" opacity="0.5"/>
          <circle cx="70" cy="50" r="6" fill="#ffaec9" opacity="0.5"/>
          <circle cx="50" cy="70" r="6" fill="#ffaec9" opacity="0.5"/>
          <circle cx="30" cy="50" r="6" fill="#ffaec9" opacity="0.5"/>
        </svg>
      </div>
      <div class="detalle-elegante detalle-1"></div>
      <div class="detalle-elegante detalle-2"></div>
    </div>

    <!-- Contenido principal -->
    <div class="contenido-principal">
      <transition name="card-slide" mode="out-in">
        <component
          :is="componenteActual"
          :key="indiceActual"
          @siguiente="irAlSiguiente"
        />
      </transition>
      
      <Navegacion 
        v-if="mostrarNavegacion"
        @atras="irAtras"
        @siguiente="irAlSiguiente"
        :puede-retroceder="indiceActual > 0"
        :puede-avanzar="indiceActual < pasos.length - 1"
      />
    </div>
  </div>
</template>

<script>
import Dos from './components/Dos.vue';
import Inicio from './components/Inicio.vue';
import Tres from './components/Tres.vue';
import Uno from './components/Uno.vue';
import Navegacion from './components/Navegacion.vue';
import Fin from './components/Fin.vue';

export default {
  components: {
    Inicio,
    Uno,
    Dos,
    Tres,
    Navegacion,
    Fin
  },
  data() {
    return {
      pasos: ["Inicio", "Uno", "Dos", "Tres", "Fin"],
      indiceActual: 0
    }
  },
  computed: {
    componenteActual() {
      return this.pasos[this.indiceActual]
    },
    mostrarNavegacion() {
      return this.indiceActual !== 0
    }
  },
  methods: {
    irAlSiguiente() {
      console.log("Se actualiza el componente a " + this.pasos[this.indiceActual]);
      if (this.indiceActual < this.pasos.length - 1) {
        this.indiceActual++
      }
    },
    irAtras() {
      console.log("Retrocediendo...");
      if (this.indiceActual > 0) {
        this.indiceActual--
      }
    }
  }
}
</script>

<style>
/* Contenedor principal con fondo degradado sofisticado */
.carta-container {
  min-height: 100vh;
  background: linear-gradient(135deg, 
    #ffe4f0 0%, 
    #ffd6e8 25%, 
    #ffeef6 50%, 
    #fff0f6 75%, 
    #ffe4f0 100%);
  position: relative;
  overflow-x: hidden;
}

/* Decoraciones laterales */
.decoracion {
  position: fixed;
  top: 0;
  height: 100vh;
  width: 120px;
  pointer-events: none;
  z-index: 0;
}

.decoracion-izquierda {
  left: 0;
}

.decoracion-derecha {
  right: 0;
}

/* Líneas decorativas verticales */
.linea-decorativa {
  position: absolute;
  width: 1px;
  height: 100%;
  background: linear-gradient(
    to bottom,
    transparent 0%,
    rgba(255, 143, 171, 0.15) 10%,
    rgba(255, 143, 171, 0.3) 50%,
    rgba(255, 143, 171, 0.15) 90%,
    transparent 100%
  );
}

.linea-1 {
  left: 30px;
}

.linea-2 {
  left: 50px;
  opacity: 0.5;
}

.decoracion-derecha .linea-1 {
  left: auto;
  right: 30px;
}

.decoracion-derecha .linea-2 {
  left: auto;
  right: 50px;
}

/* Elementos florales */
.elemento-floral {
  position: absolute;
  width: 40px;
  height: 40px;
  left: 10px;
  animation: floatFloral 6s ease-in-out infinite;
}

.floral-1 {
  top: 15%;
  animation-delay: 0s;
}

.floral-2 {
  top: 70%;
  animation-delay: 3s;
}

.decoracion-derecha .elemento-floral {
  left: auto;
  right: 10px;
}

/* Detalles elegantes (pequeños acentos) */
.detalle-elegante {
  position: absolute;
  width: 3px;
  height: 3px;
  background: #ff8fab;
  border-radius: 50%;
  left: 40px;
  opacity: 0.6;
  animation: twinkle 3s ease-in-out infinite;
}

.detalle-1 {
  top: 35%;
  animation-delay: 0.5s;
}

.detalle-2 {
  top: 55%;
  animation-delay: 2s;
}

.decoracion-derecha .detalle-elegante {
  left: auto;
  right: 40px;
}

/* Contenido principal centrado */
.contenido-principal {
  position: relative;
  z-index: 1;
  max-width: 1200px;
  margin: 0 auto;
  padding: 0 20px;
}

/* Animaciones */
@keyframes floatFloral {
  0%, 100% {
    transform: translateY(0) rotate(0deg);
    opacity: 0.5;
  }
  50% {
    transform: translateY(-15px) rotate(5deg);
    opacity: 0.8;
  }
}

@keyframes twinkle {
  0%, 100% {
    opacity: 0.3;
    transform: scale(1);
  }
  50% {
    opacity: 0.8;
    transform: scale(1.5);
  }
}

/* Animación tipo carta deslizándose */
.card-slide-enter-active {
  animation: slideInRight 0.5s ease-out;
}

.card-slide-leave-active {
  animation: slideOutLeft 0.5s ease-in;
}

@keyframes slideInRight {
  from {
    transform: translateX(100%) scale(0.8);
    opacity: 0;
  }
  to {
    transform: translateX(0) scale(1);
    opacity: 1;
  }
}

@keyframes slideOutLeft {
  from {
    transform: translateX(0) scale(1);
    opacity: 1;
  }
  to {
    transform: translateX(-100%) scale(0.8);
    opacity: 0;
  }
}

/* Responsivo - Ocultar decoraciones en pantallas pequeñas */
@media (max-width: 768px) {
  .decoracion {
    width: 60px;
  }

  .linea-1 {
    left: 15px;
  }

  .linea-2 {
    left: 25px;
  }

  .decoracion-derecha .linea-1 {
    right: 15px;
  }

  .decoracion-derecha .linea-2 {
    right: 25px;
  }

  .elemento-floral {
    width: 30px;
    height: 30px;
    left: 5px;
  }

  .decoracion-derecha .elemento-floral {
    right: 5px;
  }

  .detalle-elegante {
    left: 20px;
  }

  .decoracion-derecha .detalle-elegante {
    right: 20px;
  }
}

@media (max-width: 480px) {
  .decoracion {
    width: 40px;
  }

  .linea-decorativa {
    opacity: 0.5;
  }

  .elemento-floral {
    width: 25px;
    height: 25px;
  }
}
</style>