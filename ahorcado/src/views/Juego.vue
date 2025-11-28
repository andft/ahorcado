<template>
  <div class="fullscreen bg-main flex flex-center">

    <q-card class="gameCard q-pa-xl">
      <div class="column items-center">

        <h2 class="titulo text-white text-bold q-mb-md">
          ¡ADIVINA LA PALABRA!
        </h2>

        <div class="row justify-center q-mb-md letrasRow">
          <span
            v-for="(letra, index) in palabraEstado"
            :key="index"
            class="letra"
          >
            {{ letra }}
          </span>
        </div>

        <div class="categoria text-white q-mb-md">
          Categoría: <b>{{ categoria }}</b>
        </div>

<!--         <div class="row q-mb-lg hearts">
          <q-icon
            v-for="n in vidasMax"
            :key="n"
            :name="n <= vidas ? 'favorite' : 'favorite_border'"
            size="28px"
            :color="n <= vidas ? 'red' : 'grey-5'"
          />
        </div> -->

        <div class="teclado">
          <div class="row justify-center q-gutter-sm q-mb-sm">
            <q-btn
              v-for="letra in fila1"
              :key="letra"
              :label="letra"
              class="btnLetra"
              :color="colorLetra(letra)"
              @click="seleccionar(letra)"
              :disable="yaUsada(letra)"
            />
          </div>

          <div class="row justify-center q-gutter-sm q-mb-sm">
            <q-btn
              v-for="letra in fila2"
              :key="letra"
              :label="letra"
              class="btnLetra"
              :color="colorLetra(letra)"
              @click="seleccionar(letra)"
              :disable="yaUsada(letra)"
            />
          </div>

          <div class="row justify-center q-gutter-sm">
            <q-btn
              v-for="letra in fila3"
              :key="letra"
              :label="letra"
              class="btnLetra"
              :color="colorLetra(letra)"
              @click="seleccionar(letra)"
              :disable="yaUsada(letra)"
            />
          </div>
        </div>

        <div class="row justify-center q-gutter-md q-mt-xl">
          <q-btn
            label="Pista"
            color="blue"
            rounded
            unelevated
            class="botonPista"
            @click="mostrarPista"
          />

          <q-btn
            label="Salir"
            color="orange"
            rounded
            unelevated
            class="botonSalir"
            to="/"
          />
        </div>

      </div>
    </q-card>
  </div>
</template>

<script setup>
import { ref, computed } from "vue";

const categoria = "ANIMALES";
const palabra = "ELEFANTE";

const vidasMax = 7;
const vidas = ref(vidasMax);

const usadas = ref([]);

const fila1 = ["A", "B", "C", "D", "E", "F", "G"];
const fila2 = ["H", "I", "J", "K", "L", "M", "N", "O"];
const fila3 = ["P", "Q", "R", "S", "T", "U", "V", "W", "X", "Y", "Z"];

const palabraEstado = computed(() =>
  palabra.split("").map((letra) =>
    usadas.value.includes(letra) ? letra : "_"
  )
);

const yaUsada = (letra) => usadas.value.includes(letra);

const colorLetra = (letra) => {
  if (!usadas.value.includes(letra)) return "green";

  return palabra.includes(letra) ? "green-8" : "red";
};

const seleccionar = (letra) => {
  if (yaUsada(letra)) return;

  usadas.value.push(letra);
};

</script>


<style scoped>
.bg-main {
  background: radial-gradient(circle at top, #3ab0ff 0%, #005f95 60%, #00416d 100%);
}

.gameCard {
  width: 750px;
  max-width: 95vw;
  border-radius: 25px;
  background: linear-gradient(135deg, #0b68b7, #084c8f);
  box-shadow: 0 8px 25px rgba(0, 0, 0, 0.35);
}

.titulo {
  font-size: 30px;
}

.letrasRow .letra {
  font-size: 32px;
  margin: 0 6px;
  color: white;
  border-bottom: 3px solid white;
  padding: 4px 6px;
  width: 32px;
  text-align: center;
}

.categoria {
  font-size: 18px;
}

.btnLetra {
  font-size: 18px;
  padding: 10px 14px;
  width: 45px;
  font-weight: bold;
  border-radius: 10px;
}

.botonPista {
  width: 130px;
  font-size: 18px;
}

.botonSalir {
  width: 130px;
  font-size: 18px;
  background: linear-gradient(135deg, #ffa033, #ff6b00) !important;
  color: white;
}
</style>
