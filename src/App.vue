<template lang="html">
  
</template>

<script>
export default {
  name: 'app',
  data(){
    return {
      trivia: null
    };
  },
  components: {

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