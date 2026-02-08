<template>
  <div class="intro-container">
    <div class="card">

      <div class="header">
        <p class="desde">De: Pedro</p>
        <h1 class="title">Para Judith ✨</h1>
        <p class="ocasion">¡Feliz Cumpleaños!</p>
      </div>

      <p class="text">
        Preparé algo especial para ti en tu día.
      </p>

      <p class="text secondary">
        Espero que te guste tanto como yo disfruté haciéndolo
      </p>

      <p class="subtext">
        Toca el botón para abrir tu sorpresa 👇
      </p>

      <button class="cute-button" @click="continuar">
        <span class="button-content">
          ✨ Abrir carta ✨
        </span>
      </button>

      <!-- Decoración inferior -->
      <div class="decoration">🎂🎈🎁</div>
    </div>
  </div>
</template>

<script setup>
const emit = defineEmits(['siguiente']);

function continuar() {
  emit('siguiente');
}
</script>

<style scoped>
.intro-container {
  min-height: 100vh;
  display: flex;
  align-items: center;
  justify-content: center;
  padding: 20px;
  position: relative;
  overflow: hidden;
}

/* Efecto de fondo sutil */
.intro-container::before {
  content: '';
  position: absolute;
  width: 300px;
  height: 300px;
  border-radius: 50%;
  top: -100px;
  right: -100px;
  animation: pulse 4s ease-in-out infinite;
}

.intro-container::after {
  content: '';
  position: absolute;
  width: 250px;
  height: 250px;
  background: radial-gradient(circle, rgba(255, 214, 232, 0.3), transparent);
  border-radius: 50%;
  bottom: -80px;
  left: -80px;
  animation: pulse 5s ease-in-out infinite;
}

/* Tarjeta central */
.card {
  background: #fff;
  border-radius: 28px;
  padding: 40px 32px;
  max-width: 440px;
  width: 100%;
  text-align: center;
  box-shadow: 
    0 20px 60px rgba(231, 84, 128, 0.15),
    0 8px 20px rgba(0, 0, 0, 0.08);
  animation: floatIn 1s ease-out;
  position: relative;
  z-index: 1;
  border: 3px solid rgba(255, 174, 201, 0.2);
  background: radial-gradient(circle, rgba(255, 174, 201, 0.3), transparent);
}

/* Corazones flotantes */
.hearts {
  display: flex;
  justify-content: center;
  gap: 20px;
  margin-bottom: 20px;
}

.heart {
  font-size: 1.5rem;
  display: inline-block;
  animation: float 3s ease-in-out infinite;
}

.heart:nth-child(1) {
  animation-delay: 0s;
}

.heart:nth-child(2) {
  animation-delay: 0.5s;
}

.heart:nth-child(3) {
  animation-delay: 1s;
}

/* Header */
.header {
  margin-bottom: 24px;
}

.desde {
  font-size: 0.95rem;
  color: #999;
  font-style: italic;
  margin-bottom: 8px;
}

/* Título */
.title {
  font-size: clamp(2rem, 5vw, 2.6rem);
  background: linear-gradient(135deg, #e75480, #ff8fab);
  -webkit-background-clip: text;
  -webkit-text-fill-color: transparent;
  background-clip: text;
  margin-bottom: 8px;
  font-weight: 800;
  letter-spacing: 0.5px;
  animation: gentlePop 2s ease-in-out infinite alternate;
}

.ocasion {
  font-size: 1.3rem;
  color: #e75480;
  font-weight: 600;
  margin-top: 4px;
}

/* Texto principal */
.text {
  font-size: 1.15rem;
  color: #555;
  margin-bottom: 14px;
  line-height: 1.6;
}

.text.secondary {
  font-size: 1.05rem;
  color: #666;
  font-style: italic;
}

/* Texto secundario */
.subtext {
  font-size: 1rem;
  color: #888;
  margin-bottom: 28px;
  margin-top: 20px;
}

/* Botón mejorado */
.cute-button {
  background: linear-gradient(135deg, #ff8fab, #ff6b9d);
  color: white;
  border: none;
  border-radius: 999px;
  padding: 16px 36px;
  font-size: 1.15rem;
  font-weight: bold;
  cursor: pointer;
  box-shadow: 
    0 6px 0 #e06b8c,
    0 8px 20px rgba(255, 143, 171, 0.4);
  transition: all 0.2s ease;
  position: relative;
  overflow: hidden;
}

.button-content {
  position: relative;
  z-index: 1;
}

.cute-button::before {
  content: '';
  position: absolute;
  top: 50%;
  left: 50%;
  width: 0;
  height: 0;
  border-radius: 50%;
  background: rgba(255, 255, 255, 0.3);
  transform: translate(-50%, -50%);
  transition: width 0.6s, height 0.6s;
}

.cute-button:hover::before {
  width: 300px;
  height: 300px;
}

/* Efecto al pasar el mouse */
.cute-button:hover {
  transform: translateY(-3px) scale(1.02);
  box-shadow: 
    0 8px 0 #e06b8c,
    0 12px 25px rgba(255, 143, 171, 0.5);
}

/* Efecto al hacer click */
.cute-button:active {
  transform: translateY(4px);
  box-shadow: 
    0 2px 0 #e06b8c,
    0 4px 10px rgba(255, 143, 171, 0.3);
}

/* Decoración inferior */
.decoration {
  font-size: 1.8rem;
  margin-top: 24px;
  letter-spacing: 8px;
  opacity: 0.8;
}

/* Animaciones */
@keyframes floatIn {
  from {
    opacity: 0;
    transform: translateY(40px) scale(0.95);
  }
  to {
    opacity: 1;
    transform: translateY(0) scale(1);
  }
}

@keyframes gentlePop {
  from {
    transform: scale(1);
  }
  to {
    transform: scale(1.03);
  }
}

@keyframes float {
  0%, 100% {
    transform: translateY(0) rotate(0deg);
  }
  50% {
    transform: translateY(-10px) rotate(5deg);
  }
}

@keyframes pulse {
  0%, 100% {
    transform: scale(1);
    opacity: 0.3;
  }
  50% {
    transform: scale(1.1);
    opacity: 0.5;
  }
}

/* Responsivo extra */
@media (max-width: 400px) {
  .card {
    padding: 32px 24px;
  }

  .decoration {
    font-size: 1.5rem;
    letter-spacing: 6px;
  }
}
</style>