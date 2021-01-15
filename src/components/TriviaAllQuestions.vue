<template lang="html">
  <div>
      <ol>
          <li v-for="(question, i) in questions"> 
            <h3>{{question.question}}</h3>
            <h5>Category: {{question.category}} Difficulty: {{question.difficulty}}</h5>
            <p>List of answers will go here</p>
            <trivia-answers :correct="question.correct_answer" :incorrect="question.incorrect_answers"></trivia-answers>
          </li>
      </ol>
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