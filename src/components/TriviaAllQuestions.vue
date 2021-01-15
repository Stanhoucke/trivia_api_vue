<template lang="html">
  <div v-if="questions">
        <form v-on:submit.prevent="handleAnswers" id="generate-trivia-form">
            <ol>
                <li v-for="(question, i) in questions"> 
                    <h3 v-html="question.question"></h3>
                    <h5>Category: {{question.category}} Difficulty: {{question.difficulty}}</h5>
                    <trivia-answers :correct="question.correct_answer" :incorrect="question.incorrect_answers" :questionNumber="i"></trivia-answers>
                </li>
            </ol>
            <input type="submit" value="And your score is...">
        </form>
  </div>
</template>

<script>
import TriviaAnswers from '@/components/TriviaAnswers.vue'

export default {
    name: 'trivia-all-questions',
    data(){
        return{

        };
    },
    props: ['questions'],
    components: {
        "trivia-answers": TriviaAnswers
    }
}
</script>

<style lang="css" scoped>

</style>