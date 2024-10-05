<script setup>
import { useFavoritosStore } from "@/store/favoritos";
import { storeToRefs } from "pinia";
import { RouterLink } from "vue-router";

const useFavorito = useFavoritosStore();
const { favoritos } = storeToRefs(useFavorito);
const { remove } = useFavorito;
</script>

<template>
  <h1>Favoritos</h1>
  <p v-if="favoritos.length === 0">Sin favoritos</p>
  <ul class="list-group" v-else>
    <li class="list-group-item" v-for="poke in favoritos" :key="poke.id">
      <div>
        {{ poke.name }}
      </div>
      <div>
        <router-link
          :to="`/pokemons/${poke.name}`"
          class="btn btn-sm btn-primary me-1"
          >Más Información</router-link
        >
        <button class="btn btn-sm btn-danger" @click="remove(poke.id)">
          Eliminar
        </button>
      </div>
    </li>
  </ul>
</template>

<style lang="scss" scoped></style>
