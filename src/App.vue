<template lang="html">
  <div>
    <h1>Welcome to Vue Open Trivia!</h1>
    <trivia-all-questions :questions="trivia"></trivia-all-questions>
  </div>
</template>

<script>
import TriviaAllQuestions from '@/components/TriviaAllQuestions.vue'

export default {
  name: 'app',
  data(){           
    return {
      trivia: null
    };
  },
  components: {
    'trivia-all-questions': TriviaAllQuestions
  },
  mounted(){
    const url = `https://opentdb.com/api.php?amount=10`
    fetch(url)
    .then(res => res.json())
    .then(trivia => this.trivia = trivia.results)
  }

}
</script>

<style lang="css" scoped>

</style>