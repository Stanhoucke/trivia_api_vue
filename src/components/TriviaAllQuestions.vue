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
            selectedAnswers: [],
            finalAnswers: null
        };
    },
    props: ['questions'],
    components: {
        "trivia-answers": TriviaAnswers
    },
    mounted(){
        eventBus.$on('selected-answer', (answer) => {
            this.selectedAnswers.unshift(answer);
            console.log("got answer")
    });
    },
    methods: {
        getAnswers: function() {
            const question = this.selectedAnswers.map((number) => number[0]);
            const finalAnswers = [];

            for (let i = 0; i < question.length; i++) {
                if (question.indexOf(question[i]) === i ){
                    finalAnswers.push(this.selectedAnswers[i]);
                };
            };
            finalAnswers.sort();
            this.finalAnswers = finalAnswers;
            this.selectedAnswers = [];
            

            // for let i = 0, i < length, i++ loop?

        }
    }
}
</script>

<style lang="css" scoped>

</style>