<template>
  <h1>Ninja Reaction Time</h1>
  <button @click="start" :disabled="isPlaying">play</button>
  <Block v-if="isPlaying" :delay="delay" @end="endGame" />
  <!-- <p v-if="showResults">reaction time: {{ score }} ms</p> -->
  <Results v-if="showResults" :score="score" />
</template>

<script>
import Block from "./components/Block.vue";
import Results from "./components/Results.vue";

export default {
  name: "App",
  components: {
    Block,
    Results,
  },
  data() {
    return {
      isPlaying: false,
      delay: null,
      score: null,
      showResults: false,
    };
  },
  methods: {
    start() {
      this.delay = 200 + Math.random() * 50000;
      this.isPlaying = true;
      this.showResults = false;
      // console.log(this.delay);
    },
    endGame(reactionTime) {
      this.score = reactionTime;
      this.isPlaying = false;
      this.showResults = true;
    },
  },
};
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #8cb5e0;
  margin-top: 60px;
}
button {
  padding: 0.5rem 1rem;
  font-size: 1.2em;
  letter-spacing: 0.03em;
  border-radius: 10px;
  border: none;
  background-color: #8cb5e0;
  cursor: pointer;
}
button[disabled] {
  opacity: 0.2;
  cursor: not-allowed;
}
</style>
