<template>
  <h1>Main component</h1>
  <button @click="start" :disabled="isPlaying">Play</button>

  <div v-if="isPlaying">
    <Block :delay="delay" @timerStop="endGame" />
  </div>

  <div v-if="score > 0">
    <Results :reactionTime="score" />
  </div>
</template>

<script>
  //import HelloWorld from './components/HelloWorld.vue'
  import Block from "./components/Block.vue";
  import Results from "./components/Results.vue";

  export default {
    name: "App",
    components: {
      //HelloWorld
      Block,
      Results,
    },
    data() {
      return {
        isPlaying: false,
        delay: null,
        score: 0,
      };
    },
    methods: {
      start() {
        this.score = 0;
        this.isPlaying = true;
        this.delay = 2000 + Math.random() * 5000;
        console.log("start clicked. Delay: " + this.delay);
      },
      endGame(scoreEmited) {
        console.log("App - endGame running");
        this.score = scoreEmited;
        this.isPlaying = false;
      },
    },
    mounted() {
      console.log("App component mounted");
    },
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
