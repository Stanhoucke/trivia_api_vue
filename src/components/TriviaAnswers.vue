<template lang="html">
        <ol class="answers">
            <li v-for="(answer) in answers">
                <label :for="questionNumber" v-html="answer"></label>
                <input type="radio" :name="questionNumber" :value="answer" v-model="selectedAnswer">
            </li>
        </ol>
</template>

<script>
export default {
    name: 'trivia-answers',
    data(){
        return{
            selectedAnswer: null
        };
    },
    props: ['correct', 'incorrect', 'questionNumber'],
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