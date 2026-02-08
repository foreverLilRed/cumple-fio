<template>
    <div class="navegacion">
      <button 
        class="btn btn-atras" 
        @click="$emit('atras')"
        :disabled="!puedeRetroceder"
      >
        ← Atrás
      </button>
      
      <button 
        class="btn btn-siguiente" 
        @click="$emit('siguiente')"
        :disabled="!puedeAvanzar"
      >
        Siguiente →
      </button>
    </div>
  </template>
  
  <script setup>
  defineProps({
    puedeRetroceder: {
      type: Boolean,
      default: true
    },
    puedeAvanzar: {
      type: Boolean,
      default: true
    }
  });
  
  defineEmits(['atras', 'siguiente']);
  </script>
  
  <style scoped>
  .navegacion {
    display: flex;
    gap: 16px;
    justify-content: center;
    padding: 20px;
  }
  
  .btn {
    padding: 12px 24px;
    font-size: 1.1rem;
    font-weight: bold;
    border: none;
    border-radius: 12px;
    cursor: pointer;
    transition: all 0.3s ease;
    box-shadow: 0 4px 6px rgba(0, 0, 0, 0.1);
  }
  
  .btn:disabled {
    opacity: 0.4;
    cursor: not-allowed;
    transform: none !important;
  }
  
  .btn:not(:disabled):hover {
    transform: translateY(-2px);
    box-shadow: 0 6px 12px rgba(0, 0, 0, 0.15);
  }
  
  .btn:not(:disabled):active {
    transform: translateY(0);
  }
  
  /* Botón Atrás - Azul bebé */
  .btn-atras {
    background: #a8d8ea;
    color: #2c3e50;
  }
  
  .btn-atras:not(:disabled):hover {
    background: #8cc9de;
  }
  
  /* Botón Siguiente - Rosa suave */
  .btn-siguiente {
    background: #ffaec9;
    color: white;
  }
  
  .btn-siguiente:not(:disabled):hover {
    background: #ff8fab;
  }
  </style>