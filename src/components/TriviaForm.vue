<template lang="html">
  <div>
      <h3>Choose from the below options to generate a random game of trivia!</h3>
      <form v-on:submit.prevent="emitNewGameInfo" id="generate-trivia-form">
        <label for="amount">Number of questions: </label>
        <input type="number" min="0" name="amount" placeholder="e.g. 10" v-model="newGameInfo.amount">
        <label for="category">Pick a category: </label>
        <select name="category" v-model="newGameInfo.category">
            <option value="">Any</option>
            <option value="9">General Knowledge</option>
        </select>
        <label for="difficulty">Difficulty: </label>
        <select name="difficulty" v-model="newGameInfo.difficulty">
            <option value="">Any</option>
            <option value="easy">Easy</option>
            <option value="medium">Medium</option>
            <option value="hard">Hard</option>
        </select>
        <label for="type">Type of questions: </label>
        <select name="type" v-model="newGameInfo.type">
            <option value="">Any</option>
            <option value="multiple">Multiple Choice</option>
            <option value="boolean">True or False</option>
        </select>
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
            newGameInfo: {
                amount: 5,
                category: "",
                difficulty: "",
                type: ""
            }
        };
    },
    methods: {
        emitNewGameInfo: function(){
            eventBus.$emit('new-game-info', this.newGameInfo);
            eventBus.$emit('show-answers', false);
        }
    }

}
</script>

<style lang="css" scoped>

</style>