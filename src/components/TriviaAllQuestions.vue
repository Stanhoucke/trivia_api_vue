<template lang="html">
  <div v-if="questions">

            <ol>
                <li v-for="(question, i) in questions"> 
                    <h3 v-html="question.question"></h3>
                    <h5>Category: {{question.category}} Difficulty: {{question.difficulty}}</h5>
                    <trivia-answers :correct="question.correct_answer" :incorrect="question.incorrect_answers" :questionNumber="i"></trivia-answers>
                </li>
            </ol>
            <input type="button" value="And your score is..." v-on:click="getAnswers" id="get-answers">

  </div>
</template>

<script>
import { eventBus } from '@/main.js'
import TriviaAnswers from '@/components/TriviaAnswers.vue'

export default {
    name: 'trivia-all-questions',
    data(){
        return{
            selectedAnswers: []
        };
    },
    props: ['questions'],
    components: {
        "trivia-answers": TriviaAnswers
    },
    mounted(){
        eventBus.$on('selected-answer', (answer) => {
            this.selectedAnswers.push(answer);
            console.log("got answer")
    });
    },
    methods: {
        getAnswers: function() {
            console.log("hello")

        }
    }
}
</script>

<style lang="css" scoped>

</style>