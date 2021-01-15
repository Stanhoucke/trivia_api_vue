<template lang="html">
  <div>
    <h1>Welcome to Vue Open Trivia!</h1>
    <trivia-form></trivia-form>
    <trivia-all-questions :questions="trivia"></trivia-all-questions>
  </div>
</template>

<script>
import { eventBus } from "@/main.js";
import TriviaAllQuestions from '@/components/TriviaAllQuestions.vue';
import TriviaForm from '@/components/TriviaForm.vue';

export default {
  name: 'app',
  data(){           
    return {
      trivia: null,
      newGameInfo: null
    };
  },
  components: {
    'trivia-all-questions': TriviaAllQuestions,
    'trivia-form': TriviaForm
  },
  mounted(){
    eventBus.$on('new-game-info', (newGameInfo) => {
      this.newGameInfo = newGameInfo;
      this.fetchTriva(newGameInfo);
    });
  },
  methods: {
    fetchTriva: function(newGameInfo){
      const url = `https://opentdb.com/api.php?amount=${newGameInfo}`
      fetch(url)
      .then(res => res.json())
      .then(trivia => this.trivia = trivia.results)
    }
  }

}
</script>

<style lang="css" scoped>

</style>