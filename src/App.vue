<script setup>
import { RouterLink, RouterView } from "vue-router";
</script>

<template>
  <nav class="navbar navbar-light bg-dark">
    <div class="container">
      <router-link class="navbar-brand" to="/">
        <img src="@/assets/logo.svg" alt="" width="30" height="24" />
        PokemApi
      </router-link>
      <div>
        <router-link class="btn btn-outline-primary me-1" to="/">Home</router-link>
        <router-link class="btn btn-outline-primary" to="/pokemons">Pokemons</router-link>
      </div>
    </div>
  </nav>
  <div class="container text-center">
    <RouterView />
  </div>
</template>

<style scoped></style>
