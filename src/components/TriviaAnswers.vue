<template lang="html">
  <ol class="answers">
      <li v-for="answer in answers">
          {{answer}}
      </li>
  </ol>
</template>

<script>
export default {
    name: 'trivia-answers',
    data(){
        return{

        };
    },
    props: ['correct', 'incorrect'],
    computed: {
        answers: function(){
            let index = Math.floor(Math.random() * 4);
            const answers = this.incorrect.map(option => option);
            answers.splice(index, 0, this.correct);
            return answers;
        }
    }
}
</script>

<style lang="css" scoped>
.answers {
    list-style-type: upper-alpha;
}
</style>