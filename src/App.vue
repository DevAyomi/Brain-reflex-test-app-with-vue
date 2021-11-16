<template>
  <h2>Check Your brain reflexes</h2>

  <button @click="start" :disabled="isPlaying" type="button" class="button">
    START
  </button>

  <Block v-if="isPlaying" :delay="delay" @end="endGame"/>
  <Result v-if="show" :score="score" />
</template>

<script>
import Block from './components/Block.vue'
import Result from './components/Result.vue'

export default {
  name: 'App',
  components: {
    Block,
    Result
  },

  data(){
    return {
      isPlaying: false,
      delay: null,
      score: null,
      show: false,
    }
  },

  methods: {
    start(){
      this.delay = 2000 + Math.random() * 5000
      this.isPlaying = true
    },
    endGame(reactionTime){
      this.score = reactionTime
      this.isPlaying = false
      this.show = true
    }
  }
}
</script>

<style>

body {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #444;
  margin-top: 60px;
  height: 100%;
  display: grid;
  background: rgb(238, 174, 202);
  background: linear-gradient(30deg, rgba(238, 174, 202, 1) 0%, rgba(148, 187, 233, 1) 100%);
}

.button {
    margin: auto;
    padding: 0;
    border: none;
    border-radius: 35%;
    width: 250px;
    height: 200px;
    background: rgb(238, 174, 202);
    background: linear-gradient(30deg, rgba(238, 174, 202, 1) 0%, rgba(148, 187, 233, 1) 100%);
    color: rgba(195, 180, 216, 1);
    font-size: 3.6em;
    font-weight: 600;

    box-shadow: inset 0 0 35px 0px rgba(0, 0, 0, 0.25),
        inset 0 2px 1px 1px rgba(255, 255, 255, 0),
        1px 1px 15px 2px rgba(154, 137, 164, 0.5);

    text-shadow: 1px -1px 3px rgba(143, 162, 199, 1),
        -1px 1px 3px rgba(192, 151, 178, 1);
    outline: none;

    -webkit-transition: box-shadow 0.4s, text-shadow 0.5s;
    -moz-transition: box-shadow 0.4s, text-shadow 0.5s;
    transition: box-shadow 0.4s, text-shadow 0.5s;
}
    .button:hover {
        cursor: pointer;

        box-shadow: inset 0 0 35px 0px rgba(0, 0, 0, 0.15),
            inset 0 2px 1px 1px rgba(255, 255, 255, 0),
            1px 1px 15px 2px rgba(154, 137, 164, 0.1);

        text-shadow: 3px -3px 5px rgba(143, 162, 199, 1),
            -3px 3px 5px rgba(192, 151, 178, 1);

        -webkit-transition: box-shadow 0.4s, text-shadow 0.5s;
        -moz-transition: box-shadow 0.4s, text-shadow 0.5s;
        transition: box-shadow 0.4s, text-shadow 0.5s;
}

 .button:active {
        background: linear-gradient(
            30deg,
            rgba(210, 178, 212, 1) 0%,
            rgba(177, 183, 223, 1) 100%
        );
        color: rgba(192, 181, 218, 1);

        box-shadow: inset 0 0 10px 2px rgba(0, 0, 0, 0.15),
            1px 1px 15px 2px rgba(154, 137, 164, 0.1);

        text-shadow: 1px -1px 1px rgba(143, 162, 199, 0.75),
            -1px 1px 1px rgba(192, 151, 178, 0.75);

        -webkit-transition: background 0.3s color 0.2s,
            text-shadow 0.3s box-shadow 0.3s;
        -moz-transition: background 0.3s color 0.2s,
            text-shadow 0.3s box-shadow 0.3s;
        transition: background 0.3s color 0.2s, text-shadow 0.3s box-shadow 0.3s;
    }

</style>
