<template>
  <h1>How fast can u catch me?</h1>
  <button @click = "start" :disabled="isPlaying" :class="{bgChange:isPlaying}">Play</button>

  <div v-if="isPlaying">
    <Block :delay="delay" @endGame="endGame" :score="score"/>
  </div>

  <div v-if="end">
    <Result :score="score" />
  </div>

</template>

<script>

import Block from "./components/Block.vue"
import Result from "./components/Result.vue"

export default {
  name: 'App',

  components: {
   Block,Result
  },

  data() {
    return {
      isPlaying : false,
      delay : null,
      score : 0,
      end : false
    }
  },

  methods: {
    start(){
      this.isPlaying = true,
      this.delay = 2000 + Math.random() * 3000;
    },
    endGame(score){
      this.score = score;
      this.isPlaying = false,
      this.end = true;
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
  color: #2c3e50;
  margin-top: 60px;
}

button {
  background: #3e3eff;
  padding: 8px 20px;
  border: none;
  font-size: 20px;
  color: white;
  border-radius: 2px;
  font-weight: 600;
  cursor: pointer;
}

.bgChange{
  background: #8484ffb0;
}
</style>
