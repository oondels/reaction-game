<template>
  <div id="app">
    <h1>Reaction Timer</h1>
    <button ref="start" @click="startGame" :disabled="isPlaying">
      {{ isPlaying ? "Wait..." : "Play" }}
    </button>
    <BlockVue v-if="isPlaying" :delay="delay" @endGame="endGame" />
    <ResultsVue v-if="showResults" :score="score" />
  </div>
</template>

<script>
import BlockVue from "./components/Block.vue";
import ResultsVue from "./components/Results.vue";

export default {
  name: "App",
  components: { BlockVue, ResultsVue },

  data() {
    return {
      isPlaying: false,
      delay: null,
      score: null,
      showResults: false,
    };
  },

  methods: {
    startGame() {
      this.delay = 2000 + Math.random() * 5000;
      this.isPlaying = true;
      this.showResults = false;
      this.$refs.start.classList.toggle("playing");
    },

    endGame(reactionTime) {
      this.score = reactionTime;
      this.isPlaying = false;
      this.showResults = true;
      this.$refs.start.classList.toggle("playing");
    },
  },
};
</script>

<style scoped>
#app {
  font-family: "Avenir", Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #444;
  margin-top: 60px;
}

h1 {
  font-size: 2.5rem;
  color: #222;
  margin-bottom: 20px;
}

button {
  padding: 12px 24px;
  background-color: #21c421;
  color: #fff;
  border: none;
  border-radius: 12px;
  font-size: 1.2rem;
  cursor: pointer;
  transition: background-color 0.3s ease, transform 0.2s ease;
}

button:hover {
  background-color: #17a817;
  transform: scale(1.05);
}

button:disabled {
  background-color: #e0e0e0;
  color: #888;
  cursor: not-allowed;
}

.playing {
  cursor: not-allowed;
  background-color: #e0e0e0;
  color: #888;
}
</style>
