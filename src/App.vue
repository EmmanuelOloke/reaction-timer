<template>
  <h1>Pope Reaction Timer</h1>
  <button @click="start" :disabled="isPlaying">Play!</button>
  <BlockComponent v-if="isPlaying" :delay="delay" @end="endGame"/>
  <ResultComponent v-if="score" :score="score"/>
</template>

<script>
import BlockComponent from './components/BlockComponent.vue'
import ResultComponent from './components/ResultComponent.vue'

export default {
  name: 'App',
  components: {
    BlockComponent,
    ResultComponent,
  },
  data() {
    return {
      isPlaying: false,
      delay: null,
      score: null,
    }
  },
  methods: {
    start() {
      this.delay = 2000 + Math.random() * 5000
      this.isPlaying = true
      this.score = null
    },
    endGame(reactionTime) {
      this.score = reactionTime
      this.isPlaying = false
    }
  }
}
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #444;
  margin-top: 60px;
}

button {
  background: #0FAF87;
  color: white;
  border: none;
  padding: 8px 16px;
  border-radius: 4px;
  font-size: 16px;
  letter-spacing: 1px;
  cursor: pointer;
  margin: 10px;
}

button[disabled] {
  opacity: 0.2;
  cursor: not-allowed;
}
</style>
