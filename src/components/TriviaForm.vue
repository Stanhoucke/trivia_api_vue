<template lang="html">
  <div>
      <form v-on:submit.prevent="emitNewGameInfo" id="generate-trivia-form">
        <label for="amount">Number of questions: </label>
        <input type="number" min="0" name="amount" placeholder="e.g. 10" v-model="newGameInfo.amount">
        <label for="category">Pick a category: </label>
        <select name="category" v-model="newGameInfo.category">
            <option value="">Any</option>
            <option v-for="(category, i) in categories" :value="category">{{i}}</option>
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
      <h3 v-if="showForm">Choose from the above options to play a game of trivia!</h3>
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
            },
            showForm: true,
            categories: {
                "General Knowledge": 9,
                "Entertainment: Books": 10,
                "Entertainment: Film": 11,
                "Entertainment: Music": 12,
                "Entertainment: Musicals & Theatres": 13,
                "Entertainment: Television": 14,
                "Entertainment: Video Games": 15,
                "Entertainment: Board Games": 16,
                "Science & Nature": 17,
                "Science: Computers": 18,
                "Science: Mathematics": 19,
                Mythology: 20,
                Sports: 21,
                Geography: 22,
                History: 23,
                Politics: 24,
                Art: 25,
                Celebrities: 26,
                Animals: 27,
                Vehicles: 28,
                "Entertainment: Comics": 29,
                "Science: Gadgets": 30,
                "Entertainment: Japanese Anime & Manga": 31,
                "Entertainment: Cartoon & Animations": 32
            }
        };
    },
    methods: {
        emitNewGameInfo: function(){
            this.showForm = false;
            eventBus.$emit('new-game-info', this.newGameInfo);
            eventBus.$emit('show-answers', false);
        }
    }

}
</script>

<style lang="css" scoped>

</style>