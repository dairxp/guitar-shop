<script setup>
import { ref, reactive, onMounted } from "vue";
import { db } from "./data/guitarra";
import Guitarra from "./components/Guitarra.vue";
import Header from "./components/Header.vue";
import Footer from "./components/Footer.vue";
// const state = reactive({
//   guitarras: db,
// });

// console.log(state.guitarras);

const guitarras = ref([]);
const carrito = ref([]);
// Para datos relacioandos
// const state = reactive({
//   guitarras,
// });

onMounted(() => {
  guitarras.value = db;
  // state.guitarras = db;
});
const agregarCarrito = (guitarra) => {
  guitarra.cantidad = 1;
  carrito.value.push(guitarra);
  // numero.value++;
};
</script>

<template>
  <Header :carrito="carrito" />
  <main class="container-xl mt-5">
    <h2 class="text-center">Nuestra Colección</h2>

    <div class="row mt-5">
      <!-- AQUI -->
      <Guitarra
        v-for="guitarra in guitarras"
        :guitarra="guitarra"
        @agregar-carrito="agregarCarrito"
      />
    </div>
  </main>
  <Footer />
</template>
