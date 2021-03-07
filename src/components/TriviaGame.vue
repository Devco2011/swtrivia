<template>
  <div class="box">
    <h1>Star Wars Trivia</h1>
    <div v-for="card in trivia" :key="card.id">
      <flash-card :trivia="card" />
    </div>
  </div>
</template>

<script>
import { trivia } from "../trivia";
import FlashCard from "./FlashCard";

export default {
  components: { FlashCard },

  data() {
    return {
      trivia: [...trivia],
    };
  },
};
</script>

<style>
</style>