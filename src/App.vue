<template>
  <h1>Reaction timer 
    <!-- <small>Written by Abolfazl&Erfan</small>   -->
  </h1>
  <!-- <small>Written by Abolfazl&Erfan</small> -->
  <button @click="start" :disabled="isPlaying">play</button>
  <!-- <p v-if="showResult">Reaction: {{ score }} ms</p> -->
  <block v-if="isPlaying" :delay="delay" @end="endGame" />
  <Results v-if="showResult" :score="score" />
  <!-- <small>Written by Abolfazl&Erfan</small>  -->
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
      delay: null,
      isPlaying: false,
      score: null,
      showResult: false,
    };
  },
  methods: {
    start() {
      this.delay = 2000 + Math.random() * 5000;
      this.isPlaying = true;
      this.showResult = false;
      // console.log(th is.delay);
    },
    endGame(reactionTime) {
      this.score = reactionTime;
      this.isPlaying = false;
      this.showResult = true;
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
button{
  background: #0faf87;
  color: white;
  border: none;
  padding: 8px 16px;
  border-radius:4px ;
  font-size: 16px;
  letter-spacing: 1px;
  cursor:pointer ;
  margin: 10px;
}
button[disabled]{
  opacity: 0.2;
  cursor: not-allowed;
}

</style>
