<template>
  <div class="nivel-page row justify-center items-center q-pa-lg">

    <q-card class="nivel-card q-pa-xl">

      <!-- Título -->
      <h3 class="titulo text-white text-center q-mb-lg">
        ELIGE UN NIVEL
      </h3>

      <!-- Línea decorativa -->
      <hr class="separador" />

      <!-- Botones de niveles -->
      <div class="column items-center q-gutter-lg q-mt-md">

        <q-btn 
          class="btn-nivel facil"
          rounded
          unelevated
          @click="seleccionar('1')"
          :class="{ activo: nivelSeleccionado === '1' }"
        >
          <div class="contenido-btn">
            <span class="icono">⭐</span>
            <span class="texto">FÁCIL</span>
          </div>
        </q-btn>

        <q-btn 
          class="btn-nivel normal"
          rounded
          flat
          @click="seleccionar('2')"
          :class="{ activo: nivelSeleccionado === '2' }"
        >
          <div class="contenido-btn">
            <span class="icono">⭐⭐</span>
            <span class="texto">NORMAL</span>
          </div>
        </q-btn>

        <q-btn 
          class="btn-nivel dificil"
          rounded
          unelevated
          @click="seleccionar('3')"
          :class="{ activo: nivelSeleccionado === '3' }"
        >
          <div class="contenido-btn">
            <span class="icono">⭐⭐⭐</span>
            <span class="texto">DIFÍCIL</span>
          </div>
        </q-btn>

      </div>

      <div class="row justify-center q-mt-xl">
        <button class="btn continuar" @click="irJuego">Continuar</button>
      </div>

    </q-card>

    <img :src="nivel" alt="muñeco" class="personaje" />

  </div>
</template>

<script setup>
import { ref } from "vue";
import { useRouter } from "vue-router";
import nivel from "../assets/nivel.png";

const router = useRouter();

const nivelSeleccionado = ref(null);

const seleccionar = (nivel) => {
  nivelSeleccionado.value = nivel;
};

const irJuego = () => {
  if (!nivelSeleccionado.value) return;

  let jugadores = JSON.parse(localStorage.getItem("jugadores")) || [];
  const idActual = localStorage.getItem("jugadorActual");

  const jugador = jugadores.find(j => j.id === idActual);

  if (jugador) {
    jugador.nivel = nivelSeleccionado.value;
    localStorage.setItem("jugadores", JSON.stringify(jugadores));
  }

  router.push("/juego");
};
</script>

<style scoped>

.nivel-page {
  min-height: 100vh;
  background: radial-gradient(circle at center, #0a4c8b, #043a6b);
  background-image: url("../assets/fondoInicio.png");
  background-size: cover;
  background-position: center;
  padding: 20px;
}

.nivel-card {
  width: 600px;
  max-width: 95vw;
  border-radius: 28px;
  background: linear-gradient(180deg, rgba(32, 125, 206, 0.9), rgba(4, 90, 158, 0.92));
  border: 3px solid #8cd2ff;
  backdrop-filter: blur(4px);
  box-shadow: 0 0 35px rgba(0, 0, 0, 0.45);
  padding-bottom: 40px;
}

.titulo {
  font-size: 30px;
  font-weight: 800;
  letter-spacing: 1px;
  color: #ffffff;
  text-shadow: 0px 2px 6px rgba(0, 0, 0, 0.4);
}

.btn-nivel {
  width: 280px;
  padding: 14px 0;
  border-radius: 12px;
  text-transform: none;
  font-weight: 700;
  font-size: 20px;
  color: white;
  border: 3px solid #ffffff55;
  box-shadow: 0 6px 20px rgba(0, 0, 0, 0.35);
}

.contenido-btn {
  display: flex;
  align-items: center;
  justify-content: center;
  gap: 14px;
}

.icono img {
  width: 25px;
}

.texto {
  font-size: 20px;
  font-weight: 700;
}


.facil,
.normal,
.dificil {
  padding: 16px 0;
  font-size: 18px;
  font-weight: 700;
  border-radius: 18px;
  color: white;
  background: linear-gradient(92deg, #ff8a00, #ff5c00);
  text-shadow: 1px 1px 3px #00000055;
  box-shadow: 0px 4px 0px #00000033;
  transition: transform 0.15s ease, box-shadow 0.15s ease, background 0.3s ease;
}

/* Hover */
.facil:hover,
.normal:hover,
.dificil:hover {
  transform: translateY(-3px);
  box-shadow: 0px 7px 14px rgba(0, 0, 0, 0.4);
}

/* Activo (verde) */
.btn-nivel.activo {
  background: linear-gradient(92deg, #21c45d, #0fa144) !important;
  box-shadow: 0px 4px 10px #0d8d3eaa !important;
  color: white !important;
  border-color: #4fff6c !important;
  transform: scale(1.03);
  transition: transform 0.15s ease;
}

.continuar {
  background: #00ff1a;
  color: rgb(255, 255, 255);
  font-weight: bold;
  font-size: 20px;
  padding: 12px 28px;
  border: none;
  border-radius: 12px;
  cursor: pointer;
  font-family: "Comic Sans MS", cursive, sans-serif;
  letter-spacing: 1px;
  text-shadow: 1px 1px 2px #00000055;

  box-shadow: 0px 4px 0px #00ca07;
  transition: transform 0.1s, box-shadow 0.1s;
}

.personaje {
  width: 360px;
  margin-left: 40px;
  filter: drop-shadow(0px 0px 12px rgba(0,0,0,0.35));
}

</style>