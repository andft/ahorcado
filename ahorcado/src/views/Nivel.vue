<template>
  <div class="nivel-page row justify-center items-center q-pa-lg">
    <q-card class="nivel-card q-pa-xl">

      <h3 class="titulo text-white text-center q-mb-xl">
        ELIGE UN NIVEL
      </h3>

      <div class="column items-center q-gutter-md">

        <q-btn class="btn-nivel facil" rounded>
          <div class="contenido-btn">
            <span class="icono">⭐</span>
            <span class="texto">FÁCIL</span>
          </div>
        </q-btn>

        <q-btn class="btn-nivel normal" rounded>
          <div class="contenido-btn">
            <span class="icono">⭐⭐</span>
            <span class="texto">NORMAL</span>
          </div>
        </q-btn>

        <q-btn class="btn-nivel dificil" rounded>
          <div class="contenido-btn">
            <span class="icono">⭐⭐⭐</span>
            <span class="texto">DIFÍCIL</span>
          </div>
        </q-btn>
      </div>

      <div class="row justify-center q-mt-lg">
        <button class="btn continuar" @click="irJuego">Continuar</button>
      </div>

    </q-card>
  </div>
</template>

<script setup>
import { ref } from "vue";
import { useRouter } from "vue-router";

const router = useRouter();

const nombre = ref("");

const irJuego = () => {
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
}

.nivel-card {
  width: 600px;
  max-width: 95vw;
  border-radius: 28px;
  background: linear-gradient(180deg, #207dceee, #045a9eed);
  border: 3px solid #8cd2ff;
  backdrop-filter: blur(4px);
  box-shadow: 0px 0px 25px #00000055;
}

.titulo {
  font-size: 28px;
  font-weight: 700;
  letter-spacing: 1px;
}

.btn-nivel {
  width: 260px;
  padding: 12px 0;
  border-radius: 50px;
  text-transform: none;
  font-weight: 700;
  font-size: 20px;
  box-shadow: 0px 6px 15px #00000040;
  color: white;
  border: 3px solid #ffffff55;
}

.contenido-btn {
  display: flex;
  align-items: center;
  justify-content: center;
  gap: 12px;
}

.icono {
  font-size: 22px;
}

.texto {
  font-size: 20px;
  font-weight: 700;
}

.facil {
  background: linear-gradient(90deg, #3bd140, #1eaf27);
  border-color: #86ff9a;
}

.normal {
  background: linear-gradient(90deg, #4ab3ff, #1e77ff);
  border-color: #a8d7ff;
}

.dificil {
  background: linear-gradient(90deg, #ff8b00, #ff5f00);
  border-color: #ffd1a3;
}

.btn-azar {
  width: 170px;
  padding: 10px 20px;
  font-weight: 700;
  font-size: 18px;
  background: linear-gradient(90deg, #58a2ff, #1e77ff);
  color: white;
  box-shadow: 0px 4px 12px #00000055;
  border: 2px solid #b5ddff;
}
</style>
