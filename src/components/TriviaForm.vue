<template lang="html">
  <div>
      <h3>Choose from the below options to generate a random game of trivia!</h3>
      <form v-on:submit.prevent="emitNewGameInfo" id="generate-trivia-form">
      <input type="number" min="0" placeholder="e.g. 10" v-model="numberOfQuestions">
        <input type="submit" value="Play!">
      </form>
  </div>
</template>

<script>
import { eventBus } from "@/main.js";

export default {
    name: 'trivia-form',
    data(){
        return{
            numberOfQuestions: null
        };
    },
    methods: {
        emitNewGameInfo: function(){
            eventBus.$emit('new-game-info', this.numberOfQuestions)
        }
    }

}
</script>

<style lang="css" scoped>

</style>