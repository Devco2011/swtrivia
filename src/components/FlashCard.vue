<template>
  <div class="card" :class="{ flipped: card.answerShown }">
    <div class="card-inner">
      <div class="question">
        <h4>{{ card.question }}</h4>
        <div>
          <button @click="handleClick">Show Answer</button>
        </div>
      </div>
      <div class="answer">
        <h4>{{ card.answer }}</h4>
        <div>
          <button @click="handleClick">Show Question</button>
        </div>
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

.card-inner {
  position: relative;
  width: 100%;
  height: 100%;
  text-align: center;
  transition: transform 0.8s;
  transform-style: preserve-3d;
}

.flipped .card-inner {
  transform: rotateY(180deg);
}

.question,
.answer {
  position: absolute;
  width: 100%;
  height: 100%;
  -webkit-backface-visibility: hidden;
  backface-visibility: hidden;
}

.flipped .card-inner {
  transform: rotateY(180deg);
}

.question {
  background-color: #333;
  color: rgb(214, 211, 205);
  display: grid;
  grid-template-columns: 1fr;
  grid-template-rows: auto 60px;
}
.answer {
  background-color: rgb(214, 211, 205);
  color: #333;
  transform: rotateY(180deg);
}
</style>