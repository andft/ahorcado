<template>
  <div class="fullscreen bg-main flex flex-center ">
    <q-card class="tarjetaBienvenida q-pa-xl">
      <div class="row no-wrap items-center centrado">
        <div class="column contenidoTarjeta">
          <h4 class="titulo text-white text-center text-bold q-mb-sm">
            ¡Bienvenido a bordo!
          </h4>

          <p class="subtitulo text-white text-center q-mb-lg">
            Elige tu nombre o déjalo al azar
          </p>

          <q-input
            v-model="nombre"
            placeholder="Escribe tu nombre aquí..."
            rounded
            outlined
            class="campoNombre q-mb-lg"
            bg-color="white"
          />

          <div class="row justify-center q-gutter-md">
            <button class="btn continuar" @click="irCategorias">
              Continuar
            </button>

            <q-btn
              label="Nombre aleatorio"
              rounded
              unelevated
              class="botonAleatorio"
              @click="generarAleatorio"
            />
          </div>
        </div>
      </div>
    </q-card>
    <div>
      <img :src="confundido" alt="muñeco" class="personaje" />
    </div>
  </div>
</template>

<script setup>
import { ref } from "vue";
import { useRouter } from "vue-router";
import confundido from "../assets/nombre.png";
import { nombres as listaNombres } from "../data/datos.js";

const router = useRouter();

const nombre = ref("");

const irCategorias = () => {
  router.push("/categoria");
};

const generarAleatorio = () => {
  nombre.value = listaNombres[Math.floor(Math.random() * listaNombres.length)];
};
</script>

<style scoped>
.bg-main {
  background: radial-gradient(
    circle at top,
    #3ab0ff 0%,
    #005f95 60%,
    #00416d 100%
  );
}

.personaje {
  width: 350px;
  margin-right: 20px;
}

.tarjetaBienvenida {
  width: 650px;
  max-width: 95vw;
  border-radius: 25px;
  background: linear-gradient(135deg, #0b68b7, #084c8f);
  box-shadow: 0 8px 25px rgba(0, 0, 0, 0.35);
}

.centrado {
  display: grid;
  justify-content: center;
  align-items: center;
}

.titulo {
  font-size: 26px;
}

.subtitulo {
  font-size: 17px;
  opacity: 0.9;
}

.campoNombre {
  background: white;
  border-radius: 40px !important;
}

.botonAleatorio {
  background: linear-gradient(135deg, #ffa033, #ff6b00);
  color: white;
  padding: 10px 20px;
  font-weight: bold;
  border-radius: 20px;
}

.btn {
  padding: 10px 25px;
  border: none;
  font-size: 16px;
  border-radius: 8px;
  cursor: pointer;
  font-weight: bold;
}

.continuar {
  background: #ff9b00;
  color: white;
  font-weight: bold;
  font-size: 20px;
  padding: 12px 28px;
  border: none;
  border-radius: 12px;
  cursor: pointer;
  font-family: "Comic Sans MS", cursive, sans-serif;
  letter-spacing: 1px;
  text-shadow: 1px 1px 2px #00000055;

  box-shadow: 0px 4px 0px #c67600;
  transition: transform 0.1s, box-shadow 0.1s;
}

.continuar:active {
  transform: translateY(3px);
  box-shadow: 0px 1px 0px #c67600;
}

.continuar:hover {
  filter: brightness(1.1);
}
</style>
