<template lang="html">
    <div>
        <ol class="answers">
            <li v-for="(answer) in answers">
                <form v-on:change.prevent="emitAnswer">
                    <label :for="questionNumber" v-html="answer"></label>
                    <input type="radio" :name="questionNumber" :value="[questionNumber, answer]" v-model="selectedAnswer">

                </form>
            </li>
        </ol>
        <p class="correct-answer" v-if="showAnswers">Correct answer: {{correct}}</p>
    </div>
</template>

<script>
import { eventBus } from '@/main.js'

export default {
    name: 'trivia-answers',
    data(){
        return{
            selectedAnswer: null,
            showAnswers: false
        };
    },
    props: ['correct', 'incorrect', 'questionNumber'],
    mounted() {
        eventBus.$on('show-answers', show => this.showAnswers = show);
    },
    computed: {
        answers: function(){
            let index = Math.floor(Math.random() * 4);
            const answers = this.incorrect.map(option => option);
            answers.splice(index, 0, this.correct);
            return answers;
        }
    },
    methods: {
        emitAnswer: function(){
            eventBus.$emit('selected-answer', this.selectedAnswer)
        }
    }
}
</script>

<style lang="css" scoped>
.answers {
    list-style-type: upper-alpha;
}

.correct-answer {
    background-color: mediumspringgreen;
}
</style>