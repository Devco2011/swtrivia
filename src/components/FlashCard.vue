<template>
  <div class="card" :class="{ flipped: card.answerShown }">
    <div class="card-inner">
      <div class="question">
        <h4>Hello</h4>
        <div>
          <button @click="handleClick">Show Answer</button>
        </div>
      </div>
      <div class="answer">
        <h4>Answer</h4>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  props: ["card"],
  methods: {
    handleClick() {
      this.$emit("toggle", this.card);
    },
  },
};
</script>

<style>
.card {
  background-color: transparent;
  width: 300px;
  height: 200px;
  border: 1px solid #f1f1f1;
  perspective: 1000px;
  margin-top: 20px;
}

.flipped .card-inner {
  transform: rotateY(180deg);
}
</style>