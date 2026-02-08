<template>
    <div class="fin-container">
      <!-- Confeti decorativo -->
      <div class="confeti-container">
        <div class="confeti" v-for="n in 30" :key="n" :style="getConfettiStyle(n)"></div>
      </div>
  
      <!-- GIF central grande -->
      <div class="gif-principal-wrapper">
        <div class="circulo-decorativo circulo-1"></div>
        <div class="circulo-decorativo circulo-2"></div>
        <div class="circulo-decorativo circulo-3"></div>
        <img src="/src/assets/gifs/abrazo.gif" alt="Abrazo" class="gif-principal" />
      </div>
  
      <!-- Mensaje de despedida -->
      <div class="mensaje-despedida">
        <div class="texto-principal">
          <h1 class="titulo-fin">Te deseo lo mejor</h1>
        </div>
  
        <div class="firma-final">
          <p class="texto-firma">Tu amigo,</p>
          <p class="nombre-firma">Pedro</p>
          <div class="firma-decoracion">
            <div class="linea-firma"></div>
          </div>
        </div>
      </div>
  
      <!-- Mensaje extra -->
      <div class="mensaje-extra">
        <p>¡Feliz cumpleaños, Judith! 🎂🎉</p>
      </div>
    </div>
  </template>
  
  <script setup>
  const getConfettiStyle = (n) => {
    const colors = ['#ff8fab', '#ffaec9', '#e75480', '#ffd6e8', '#a8d8ea'];
    return {
      left: `${Math.random() * 100}%`,
      animationDelay: `${Math.random() * 5}s`,
      backgroundColor: colors[Math.floor(Math.random() * colors.length)],
      animationDuration: `${3 + Math.random() * 4}s`
    };
  };
  </script>
  
  <style scoped>
  .fin-container {
    min-height: 100vh;
    display: flex;
    flex-direction: column;
    align-items: center;
    justify-content: center;
    padding: 40px 20px;
    position: relative;
    overflow: hidden;
  }
  
  /* Confeti animado */
  .confeti-container {
    position: absolute;
    top: 0;
    left: 0;
    width: 100%;
    height: 100%;
    pointer-events: none;
    overflow: hidden;
  }
  
  .confeti {
    position: absolute;
    width: 10px;
    height: 10px;
    top: -20px;
    opacity: 0.8;
    animation: caerConfeti linear infinite;
  }
  
  @keyframes caerConfeti {
    0% {
      transform: translateY(0) rotate(0deg);
      opacity: 1;
    }
    100% {
      transform: translateY(100vh) rotate(720deg);
      opacity: 0;
    }
  }
  
  /* GIF principal con círculos decorativos */
  .gif-principal-wrapper {
    position: relative;
    margin-bottom: 50px;
    animation: aparecer 1s ease-out;
  }
  
  .gif-principal {
    width: 280px;
    height: 280px;
    border-radius: 50%;
    object-fit: cover;
    border: 6px solid white;
    box-shadow: 
      0 15px 50px rgba(231, 84, 128, 0.4),
      0 0 0 12px rgba(255, 143, 171, 0.2),
      0 0 0 24px rgba(255, 174, 201, 0.1);
    position: relative;
    z-index: 2;
    animation: flotar 3s ease-in-out infinite;
  }
  
  .circulo-decorativo {
    position: absolute;
    border-radius: 50%;
    border: 2px solid;
    opacity: 0.3;
  }
  
  .circulo-1 {
    width: 320px;
    height: 320px;
    border-color: #ff8fab;
    top: 50%;
    left: 50%;
    transform: translate(-50%, -50%);
    animation: rotarCirculo 15s linear infinite;
  }
  
  .circulo-2 {
    width: 360px;
    height: 360px;
    border-color: #ffaec9;
    top: 50%;
    left: 50%;
    transform: translate(-50%, -50%);
    animation: rotarCirculo 20s linear infinite reverse;
  }
  
  .circulo-3 {
    width: 400px;
    height: 400px;
    border-color: #ffd6e8;
    top: 50%;
    left: 50%;
    transform: translate(-50%, -50%);
    animation: rotarCirculo 25s linear infinite;
  }
  
  /* Mensaje de despedida */
  .mensaje-despedida {
    text-align: center;
    animation: aparecer 1.2s ease-out 0.3s backwards;
    z-index: 2;
  }
  
  .texto-principal {
    margin-bottom: 40px;
  }
  
  .titulo-fin {
    font-size: clamp(2.5rem, 6vw, 4rem);
    background: linear-gradient(135deg, #e75480, #ff8fab, #ffaec9);
    -webkit-background-clip: text;
    -webkit-text-fill-color: transparent;
    background-clip: text;
    font-weight: 900;
    letter-spacing: 2px;
    margin-bottom: 20px;
    animation: brillar 2s ease-in-out infinite;
    text-shadow: 0 4px 20px rgba(231, 84, 128, 0.3);
  }
  
  .corazones-linea {
    font-size: 2rem;
    letter-spacing: 10px;
    animation: latirCorazones 1.5s ease-in-out infinite;
  }
  
  /* Firma final */
  .firma-final {
    background: white;
    padding: 30px 50px;
    border-radius: 20px;
    box-shadow: 
      0 10px 40px rgba(0, 0, 0, 0.1),
      0 0 0 1px rgba(255, 143, 171, 0.2);
    display: inline-block;
  }
  
  .texto-firma {
    font-size: 1.2rem;
    color: #888;
    font-style: italic;
    margin-bottom: 10px;
  }
  
  .nombre-firma {
    font-size: 3rem;
    color: #e75480;
    font-weight: 900;
    font-family: 'Brush Script MT', 'Segoe Script', cursive;
    margin-bottom: 15px;
    animation: escribir 2s ease-out;
  }
  
  .firma-decoracion {
    display: flex;
    align-items: center;
    gap: 12px;
    justify-content: center;
    margin-top: 10px;
  }
  
  .estrella {
    font-size: 1.5rem;
    animation: brillarEstrella 1.5s ease-in-out infinite;
  }
  
  .estrella:last-child {
    animation-delay: 0.75s;
  }
  
  .linea-firma {
    flex: 1;
    height: 2px;
    background: linear-gradient(
      90deg,
      transparent,
      #ff8fab 50%,
      transparent
    );
    min-width: 150px;
  }
  
  /* Mensaje extra */
  .mensaje-extra {
    margin-top: 40px;
    animation: aparecer 1.4s ease-out 0.6s backwards;
    z-index: 2;
  }
  
  .mensaje-extra p {
    font-size: 1.5rem;
    color: #e75480;
    font-weight: 700;
    background: white;
    padding: 15px 30px;
    border-radius: 50px;
    box-shadow: 0 8px 25px rgba(231, 84, 128, 0.2);
    display: inline-block;
  }
  
  /* Animaciones */
  @keyframes aparecer {
    from {
      opacity: 0;
      transform: translateY(30px) scale(0.9);
    }
    to {
      opacity: 1;
      transform: translateY(0) scale(1);
    }
  }
  
  @keyframes flotar {
    0%, 100% {
      transform: translateY(0);
    }
    50% {
      transform: translateY(-20px);
    }
  }
  
  @keyframes rotarCirculo {
    from {
      transform: translate(-50%, -50%) rotate(0deg);
    }
    to {
      transform: translate(-50%, -50%) rotate(360deg);
    }
  }
  
  @keyframes brillar {
    0%, 100% {
      filter: brightness(1);
    }
    50% {
      filter: brightness(1.2);
    }
  }
  
  @keyframes latirCorazones {
    0%, 100% {
      transform: scale(1);
    }
    50% {
      transform: scale(1.1);
    }
  }
  
  @keyframes escribir {
    from {
      opacity: 0;
      transform: translateX(-20px);
    }
    to {
      opacity: 1;
      transform: translateX(0);
    }
  }
  
  @keyframes brillarEstrella {
    0%, 100% {
      transform: scale(1) rotate(0deg);
      opacity: 0.7;
    }
    50% {
      transform: scale(1.3) rotate(180deg);
      opacity: 1;
    }
  }
  
  /* Responsivo */
  @media (max-width: 768px) {
    .gif-principal {
      width: 220px;
      height: 220px;
    }
  
    .circulo-1 {
      width: 260px;
      height: 260px;
    }
  
    .circulo-2 {
      width: 300px;
      height: 300px;
    }
  
    .circulo-3 {
      width: 340px;
      height: 340px;
    }
  
    .firma-final {
      padding: 25px 35px;
    }
  
    .nombre-firma {
      font-size: 2.5rem;
    }
  
    .mensaje-extra p {
      font-size: 1.3rem;
      padding: 12px 25px;
    }
  }
  
  @media (max-width: 480px) {
    .gif-principal {
      width: 180px;
      height: 180px;
    }
  
    .firma-final {
      padding: 20px 30px;
    }
  
    .nombre-firma {
      font-size: 2rem;
    }
  
    .linea-firma {
      min-width: 100px;
    }
  
    .corazones-linea {
      font-size: 1.5rem;
      letter-spacing: 6px;
    }
  }
  </style>