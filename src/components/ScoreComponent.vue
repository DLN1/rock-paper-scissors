<template>
  <div class="score-container">
    <h1>ROCK<br />PAPER<br />SCISSORS.</h1>
    <div class="currentScore-container">
      <div>SCORE</div>
      <div>{{ score }}</div>
    </div>
  </div>
</template>

<script setup>
import { defineProps, toRefs } from "vue";

const props = defineProps({ score: Number });

const { score } = toRefs(props);
</script>

<style scoped>
.score-container {
  border: 3px solid rgba(255, 255, 255, 0.285);
  border-radius: 5px;
  margin: 2rem;
  padding: 1.5rem;
  display: flex;
  justify-content: space-between;
}

.score-container > h1 {
  line-height: 6vmin;
  font-size: 6.5vmin;
  font-weight: 700;
  text-shadow: 0px 3px 3px rgba(0, 0, 0, 0.196706);
}

.score-container > .currentScore-container {
  background: white;
  width: 21vmin;
  display: flex;
  flex-direction: column;
  align-items: center;
  justify-content: center;
  box-shadow: 0px 3px 3px rgba(0, 0, 0, 0.196706);
  border-radius: 4px;
}
.score-container > .currentScore-container > div:first-of-type {
    color: #2A45C2;
  font-size: 3.25vmin;
}

.score-container > .currentScore-container > div:last-of-type {
    color: #565468;
  font-size: 11vmin;
  font-weight: 700;
}
</style>
