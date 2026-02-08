<template>
  <div class="contenedor">
    <!-- Header con GIF -->
    <div class="header-section">
      <div class="gif-wrapper">
        <img src="/src/assets/gifs/familia.gif" alt="Familia" class="gif" />
        <div class="gif-glow"></div>
      </div>
    </div>

    <!-- Contenido de la carta -->
    <section class="carta-section">

      <h2 class="titulo-carta">Mis deseos para ti</h2>
      
      <div class="texto-contenedor">
        <p class="parrafo">
          Te deseo de corazón que este nuevo año esté lleno de <strong>calma, 
          alegrías sinceras</strong> y momentos que te hagan sentir orgullosa 
          de todo lo que eres.
        </p>
        
        <p class="parrafo">
          Que nunca te falten <em>razones para sonreír</em>, ni personas que 
          sepan valorar tu forma tan bonita de cuidar y estar presente.
        </p>
        
        <p class="parrafo destacado">
          Gracias por todo lo que das, por lo que enseñas y por la 
          <span class="resaltado">energía tan humana que aportas cada día</span>. 
        </p>

        <p class="parrafo final">
          Y, en parte, gracias por mantenernos unidos en el trabajo, porque eso 
          también habla de tu compromiso y de tu corazón
        </p>
      </div>
    </section>
  </div>
</template>

<style scoped>
.contenedor {
  padding: 40px 20px;
  display: flex;
  flex-direction: column;
  align-items: center;
}

/* Header con GIF */
.header-section {
  margin-bottom: 40px;
  animation: fadeInDown 0.8s ease-out;
}

.gif-wrapper {
  position: relative;
  display: inline-block;
}

.gif {
  width: 200px;
  height: 200px;
  border-radius: 50%;
  object-fit: cover;
  border: 4px solid #ff8fab;
  box-shadow: 
    0 8px 25px rgba(255, 143, 171, 0.3),
    0 0 0 8px rgba(255, 255, 255, 0.5);
  animation: gentleBounce 2s ease-in-out infinite;
}

.gif-glow {
  position: absolute;
  top: 50%;
  left: 50%;
  transform: translate(-50%, -50%);
  width: 220px;
  height: 220px;
  border-radius: 50%;
  background: radial-gradient(circle, rgba(255, 143, 171, 0.2), transparent 70%);
  animation: pulse 2s ease-in-out infinite;
  pointer-events: none;
}

/* Sección de la carta */
.carta-section {
  background: white;
  border-radius: 20px;
  padding: 48px 40px;
  max-width: 650px;
  width: 100%;
  box-shadow: 
    0 10px 40px rgba(0, 0, 0, 0.08),
    0 0 0 1px rgba(255, 143, 171, 0.1);
  animation: fadeInUp 0.8s ease-out 0.2s backwards;
  position: relative;
}

.carta-section::before {
  content: '';
  position: absolute;
  top: 0;
  left: 0;
  right: 0;
  height: 5px;
  background: linear-gradient(90deg, #ff8fab, #ffaec9, #ff8fab);
  border-radius: 20px 20px 0 0;
}

/* Decoraciones de la carta */
.carta-decoracion {
  display: flex;
  align-items: center;
  gap: 16px;
  margin: 24px 0;
}

.carta-decoracion.top {
  margin-top: 0;
  margin-bottom: 32px;
}

.carta-decoracion.bottom {
  margin-top: 32px;
  margin-bottom: 0;
}

.ornamento {
  font-size: 1.3rem;
  animation: sparkle 2s ease-in-out infinite;
}

.linea-decorativa {
  flex: 1;
  height: 1px;
  background: linear-gradient(
    90deg,
    transparent,
    rgba(255, 143, 171, 0.3) 50%,
    transparent
  );
}

/* Título */
.titulo-carta {
  font-size: clamp(1.6rem, 4vw, 2rem);
  color: #e75480;
  text-align: center;
  margin-bottom: 28px;
  font-weight: 700;
  letter-spacing: 0.5px;
}

/* Contenedor de texto */
.texto-contenedor {
  line-height: 1.8;
}

.parrafo {
  font-size: 1.1rem;
  color: #444;
  margin-bottom: 20px;
  text-align: justify;
}

.parrafo strong {
  color: #e75480;
  font-weight: 600;
}

.parrafo em {
  color: #ff8fab;
  font-style: italic;
}

.parrafo.destacado {
  margin-top: 28px;
  padding: 20px;
  background: linear-gradient(135deg, #fff0f6, #ffeef6);
  border-left: 4px solid #ff8fab;
  border-radius: 8px;
  font-size: 1.15rem;
  font-weight: 500;
  margin-bottom: 20px;
}

.parrafo.final {
  margin-top: 20px;
  font-size: 1.1rem;
  color: #555;
  font-style: italic;
}

.resaltado {
  color: #e75480;
  font-weight: 700;
  position: relative;
  display: inline-block;
}

/* Animaciones */
@keyframes fadeInDown {
  from {
    opacity: 0;
    transform: translateY(-30px);
  }
  to {
    opacity: 1;
    transform: translateY(0);
  }
}

@keyframes fadeInUp {
  from {
    opacity: 0;
    transform: translateY(30px);
  }
  to {
    opacity: 1;
    transform: translateY(0);
  }
}

@keyframes gentleBounce {
  0%, 100% {
    transform: translateY(0);
  }
  50% {
    transform: translateY(-10px);
  }
}

@keyframes pulse {
  0%, 100% {
    transform: translate(-50%, -50%) scale(1);
    opacity: 0.5;
  }
  50% {
    transform: translate(-50%, -50%) scale(1.1);
    opacity: 0.8;
  }
}

@keyframes sparkle {
  0%, 100% {
    transform: scale(1) rotate(0deg);
    opacity: 0.8;
  }
  50% {
    transform: scale(1.2) rotate(10deg);
    opacity: 1;
  }
}

/* Responsivo */
@media (max-width: 768px) {
  .contenedor {
    padding: 30px 16px;
  }

  .gif {
    width: 160px;
    height: 160px;
  }

  .gif-glow {
    width: 180px;
    height: 180px;
  }

  .carta-section {
    padding: 36px 28px;
  }

  .parrafo {
    font-size: 1.05rem;
    text-align: left;
  }

  .parrafo.destacado {
    font-size: 1.1rem;
    padding: 16px;
  }
}

@media (max-width: 480px) {
  .gif {
    width: 140px;
    height: 140px;
  }

  .carta-section {
    padding: 28px 20px;
  }

  .titulo-carta {
    margin-bottom: 20px;
  }
}
</style>