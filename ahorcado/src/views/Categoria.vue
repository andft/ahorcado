<template>
  <div class="categorias row justify-center items-center q-pa-lg">
    <q-card class="cardCategorias q-pa-xl">

      <h3 class="titulo text-white text-center q-mb-xl">
        ELIGE UNA CATEGORÍA
      </h3>

      <div class="botones">
        <q-btn class="botonCategoria naranja" label="🐵 ANIMALES" />
        <q-btn class="botonCategoria azul" label="🌎 PAÍSES" />

        <q-btn class="botonCategoria azul" label="🚌 TRANSPORTES" />
        <q-btn class="botonCategoria naranja" label="🍎 ALIMENTOS" />

        <q-btn class="botonCategoria azul" label="⚽ DEPORTES" />
        <q-btn class="botonCategoria naranja" label="🎞️ PELÍCULAS" />
      </div>

      <div class="row justify-center q-mt-lg">
        <button class="btn continuar" @click="irNivel">Continuar</button>
      </div>

    </q-card>
  </div>
</template>

<script setup>
import { ref } from "vue";
import { useRouter } from "vue-router";

const router = useRouter();

const nombre = ref("");

const irNivel = () => {
  router.push("/nivel");
};
</script>

<style scoped>
.categorias {
  min-height: 100vh;
  background: radial-gradient(circle at center, #0a4c8b, #043a6b);
}

.cardCategorias {
  width: 650px;
  max-width: 95vw;
  border-radius: 30px;
  background: linear-gradient(180deg, #1e90ff, #005b9f);
  box-shadow: 0 0 25px #00000055;
  border: 3px solid #45b0ff;
}

.titulo {
  font-size: 28px;
  letter-spacing: 1px;
  font-weight: 700;
}

.botones {
  display: grid;
  grid-template-columns: 1fr 1fr;
  gap: 22px;
}

.botonCategoria {
  width: 100%;
  padding: 14px 0;
  font-size: 18px;
  font-weight: 700;
  border-radius: 18px;
  color: white;
  text-shadow: 1px 1px 2px #00000055;
  box-shadow: 0px 4px 0px #00000044;
  background: linear-gradient(90deg, #ff8b00, #ff5f00);
}


.continuar {
  background: linear-gradient(90deg, #ffb200, #ff7a00);
  color: white;
  padding: 12px 30px;
  font-size: 16px;
  font-weight: 700;
  border-radius: 18px;
  text-shadow: 1px 1px 2px #00000055;
  box-shadow: 0px 4px 0px #c67600;
}
</style>
