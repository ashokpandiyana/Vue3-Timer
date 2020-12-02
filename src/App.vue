<template>
  <h1>Reaction Time Game</h1>
  <button v-on:click="start" v-bind:disabled="isPlaying" class="square_btn">
    Play
  </button>
  <Block v-if="isPlaying" v-bind:delay="delay" @end="endGame"></Block>
  <div v-if="score">
    <results :value="score"></results>
  </div>
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
    };
  },
  methods: {
    start() {
      this.isPlaying = true;
      this.delay = 2000 + Math.random() * 5000;
    },
    endGame(reactionTime) {
      this.score = reactionTime;
      this.isPlaying = false;
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
  color: #444;
  margin-top: 60px;
}
.square_btn {
  display: inline-block;
  text-decoration: none;
  color: #fff;
  width: 120px;
  height: 50px;
  text-align: center;
  vertical-align: middle;
  overflow: hidden;
  background-image: linear-gradient(45deg, #709dff 0%, #91fdb7 100%);
  transition: 0.4s;
  border: none;
  outline: none;
  cursor: pointer;
}
</style>
