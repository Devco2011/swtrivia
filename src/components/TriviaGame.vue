<template>
  <div class="box">
    <h1>Star Wars Trivia</h1>
    <button @click="hideAll" class="flat-button">HIDE ALL</button>
    <div class="difficultyOptions">
      <difficulty-options
        :difficulty="selectedDifficulty"
        @difficultyChange="handleDifficultyChange"
      />
    </div>
    <div v-for="card in displayedTrivia" :key="card.id">
      <flash-card :card="card" @toggle="handleToggle" />
    </div>
  </div>
</template>

<script>
import trivia from "../trivia";
import FlashCard from "./FlashCard";
import DifficultyOptions from "./DifficultyOptions.vue";

export default {
  components: { FlashCard, DifficultyOptions },

  data() {
    return {
      trivia: [...trivia],
      selectedDifficulty: "all",
    };
  },

  methods: {
    handleToggle(card) {
      card.answerShown = !card.answerShown;
    },
    handleDifficultyChange(difficulty) {
      this.selectedDifficulty = difficulty;
    },
    hideAll() {
      this.trivia.forEach((t) => (t.answerShown = false));
    },
  },

  computed: {
    displayedTrivia() {
      if (this.selectedDifficulty === "all") {
        return this.trivia;
      }
      return this.trivia.filter(
        (t) => t.difficulty === this.selectedDifficulty
      );
    },
  },
};
</script>

<style>
</style>