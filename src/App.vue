<template>
  <h1>Reaction timer game</h1>
  <button @click="startGame" :disabled="isPlaying">Play</button>
  <Block v-if="isPlaying" :delay="delay" @end="endGame" />
  <Result :score="score" v-if="isDone"/>
</template>

<script>
import Block from "./components/Block";
import Result from './components/Result'

export default {
  name: "App",
  components: { Block, Result },
  data() {
    return {
      isPlaying: false,
      delay: null,
      score: null,
      isDone: false
    }
  },
  methods: {
    startGame() {
      this.delay = 2000 + Math.random() * 5000
      this.isPlaying = true;
      this.isDone = false
      console.log(this.delay)
    },
    endGame(reactionTime) {
      this.score = reactionTime
      this.isPlaying = false
      this.isDone = true
    },
  }
};
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
