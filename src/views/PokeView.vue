<script setup>
import { useRoute, useRouter } from "vue-router";
import { useGetData } from "@/composables/getData";

const route = useRoute();
const router = useRouter();
const { data, getData, loading, error } = useGetData();

getData(`https://pokeapi.co/api/v2/pokemon/${route.params.name}`);

const back = () => {
  router.push("/pokemons");
};
</script>

<template>
  <main class="text-center">
    <p v-if="loading">Cargando información...</p>
    <div class="alert alert-danger mt-2" v-if="error">{{ error }}</div>
    <div v-else>
      <div v-if="data">
        <img :src="data.sprites?.front_default" alt="" />
        <h1>Poke: {{ $route.params.name }}</h1>
      </div>
      <h1 v-else>Pokemon no encontrado...</h1>
      <button @click="back()" class="btn btn-outline-primary">
        Volver al listado
      </button>
    </div>
  </main>
</template>
