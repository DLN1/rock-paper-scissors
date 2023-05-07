<template>
  <RulesModal v-if="showModal" @closeModal="showModal = !showModal" />
  <ScoreComponent :score='score' />
  <div class="container">
    <div class="game-container">
      <template v-if="!selectedOption">
        <div v-for="(option, i) in options" :key="i">
          <HandComponent @optionPicked="randomResult" :option="option" />
        </div>
      </template>
      <template v-else>
        <div class="result-wrapper">
          <div class="picks">
            <h6>YOU PICKED</h6>
            <HandComponent :option="selectedOption" />
          </div>
          <div class="result">
            <h1>{{ winner }}</h1>
            <button @click="reset">PLAY AGAIN</button>
          </div>
          <div class="picks">
            <h6>THE HOUSE PICKED</h6>
            <HandComponent :option="houseSelectedOption" />
          </div>
        </div>
      </template>
    </div>
  </div>
  <div v-if="!selectedOption && !houseSelectedOption" class="rules">
    <button @click="showModal = !showModal" class="rules-btn">Rules</button>
  </div>
</template>

<script setup>
import { ref, toRaw } from "vue";
import ScoreComponent from "./components/ScoreComponent.vue";
import HandComponent from "./components/HandComponent.vue";
import RulesModal from "./components/RulesModal.vue";

const paperIcon = require("@/assets/paperIcon.svg");
const scissorsIcon = require("@/assets/scissorsIcon.svg");
const rockIcon = require("@/assets/rockIcon.svg");

const selectedOption = ref(null);
const houseSelectedOption = ref(null);
const winner = ref(null);
const score = ref(0);
const options = ref([
  {
    name: "paper",
    icon: paperIcon,
    color: "#4664F4",
  },
  {
    name: "scissors",
    icon: scissorsIcon,
    color: "#EB9F0E",
  },
  {
    name: "rock",
    icon: rockIcon,
    color: "#DB2E4D",
  },
]);

const showModal = ref(false);

const randomResult = (e) => {
  selectedOption.value = toRaw(e);
  houseSelectedOption.value = options.value[Math.floor(Math.random() * 3)];

  checkWinner()
};

const checkWinner = () => {
  console.log(selectedOption.value.name)
  if (selectedOption.value.name === 'rock' && houseSelectedOption.value.name === 'scissors') {
    winner.value = "YOU WIN"
    score.value++;
  } else if (selectedOption.value.name === 'paper' && houseSelectedOption.value.name === 'rock') {
    winner.value = "YOU WIN"
    score.value++;
  } else if (selectedOption.value.name === 'scissors' && houseSelectedOption.value.name === 'paper') {
    winner.value = "YOU WIN"
    score.value++;
  } else if (selectedOption.value.name === 'rock' && houseSelectedOption.value.name === 'paper') {
    winner.value = "YOU LOSE"
  } else if (selectedOption.value.name === 'paper' && houseSelectedOption.value.name === 'scissors') {
    winner.value = "YOU LOSE"

  } else if (selectedOption.value.name === 'scissors' && houseSelectedOption.value.name === 'rock') {
    winner.value = "YOU LOSE"

  } else {
    winner.value = "DRAW"
  }
}

const reset = () => {
  selectedOption.value = null;
  houseSelectedOption.value = null;
};
</script>

<style>
@import url("https://fonts.googleapis.com/css2?family=Barlow+Semi+Condensed:wght@600;700&display=swap");
body {
  background: radial-gradient(
    134.34% 134.34% at 50% 0%,
    #1f3757 0%,
    #131537 100%
  );
  background-repeat: no-repeat;
  min-height: 100vh;
  overflow-x: hidden;
  font-family: "Barlow Semi Condensed", sans-serif;
  font-weight: 600;
  color: white;
}
* {
  padding: 0;
  margin: 0;
  box-sizing: border-box;
}

.container {
  display: flex;
  align-items: center;
  justify-content: center;
  max-height: 100vh;
}

.game-container {
  display: flex;
  align-items: center;
  justify-content: center;
  height: 100%;
  flex-wrap: wrap;
  gap: 30px;
  margin-top: 5rem;
}

.game-container > div {
  flex-basis: 33%;
  display: flex;
  justify-content: center;
}

.rules {
  display: flex;
  justify-content: flex-end;
  margin-right: 2rem;
}

.rules-btn {
  margin-top: 50px;
  border: 1px solid white;
  color: white;
  text-transform: uppercase;
  font-size: 16px;
  letter-spacing: 2.5px;
  padding: 11px 36px;
  border-radius: 8px;
  font-family: "Barlow Semi Condensed", sans-serif;
  background: transparent;
}

.rules-btn:hover {
  background: white;
  color: #1f3757;
  cursor: pointer;
}

.result-wrapper > .picks {
  display: flex;
  flex-direction: column;
  align-items: center;
  gap: 40px;
  font-size: 24px;
  line-height: 32px;
  letter-spacing: 3px;
}

.result-wrapper > .result {
  display: flex;
  flex-direction: column;
  min-width: 300px;
  align-items: center;
  justify-content: center;
  margin: 0px 50px;
}

.result-wrapper > .result > h1 {
  font-size: 56px;
}

.result-wrapper > .result > button {
  margin-top: 20px;
  width: 100%;
  height: 48px;
  color: #3b4262;
  font-family: "Barlow Semi Condensed", sans-serif;
  letter-spacing: 2.5px;
}
</style>
