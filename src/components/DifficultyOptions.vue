<template>
  <div>
    <button
      :class="{ active: difficulty === 'easy' }"
      @click="selectDifficulty('easy')"
    >
      Easy
    </button>
    <button
      :class="{ active: difficulty === 'easy' }"
      @click="selectDifficulty('medium')"
    >
      Medium
    </button>
    <button
      :class="{ active: difficulty === 'easy' }"
      @click="selectDifficulty('hard')"
    >
      Hard
    </button>
    <button
      :class="{ active: difficulty === 'all' }"
      @click="selectDifficulty('all')"
    >
      All
    </button>
  </div>
</template>

<script>
export default {
  props: ["difficulty"],
  methods: {
    selectDifficulty(difficulty) {
      this.$emit("difficultyChange", difficulty);
    },
  },
};
</script>

<style>
</style>