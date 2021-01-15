<template lang="html">
  <ol>
      <li>
          {{correct}}
      </li>
      <li v-for="option in incorrect">
          {{option}}
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
    props: ['correct', 'incorrect']
}
</script>

<style lang="css" scoped>

</style>