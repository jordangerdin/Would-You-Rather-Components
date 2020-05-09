<template>
    <div id="app">
        <h1 class="title">Would You Rather...?</h1>
        
        <WouldYouRatherQuestion
            v-for = "question in questions" 
            v-bind:key="question.id"
            v-bind:question="question.question"
            v-on:answer-changed="questionAnswered"
            v-bind:id = "question.id"
            v-bind:answer1 = "question.answer1"
            v-bind:answer2 = "question.answer2"
            >
        </WouldYouRatherQuestion>

        <div class="" id="answers">
            <h2>You chose...</h2>
            <ul v-for = "answer in answers" 
                v-bind:key="answer.index">
                <li v-show = "answer">{{ answer }}</li>
            </ul>
        </div>

    </div>
</template>

<script>
import WouldYouRatherQuestion from './components/WouldYouRatherQuestion.vue'

export default {
    name: 'app',
    components: {
        WouldYouRatherQuestion
    },
    data() {
        return {
            questions: [
                {
                    id: 0,
                    question: '...Would you rather live in a castle or a spaceship traveling far from earth?',
                    answer1: 'a castle',
                    answer2: 'a spaceship',
                },
                {
                    id: 1,
                    question: '...Would you rather be able to control fire or water?',
                    answer1: 'fire',
                    answer2: 'water'
                },
                {
                    id: 2,
                    question: '...Would you rather go skydiving or scubadiving?',
                    answer1: 'skydiving',
                    answer2: 'scubadiving'
                }
            ],
            answers: ['', '', ''],
            answer: '',
            filled: false
        }
    },
    methods: {
        questionAnswered(answerId, answer) {
            this.$set(this.answers, answerId, answer)
        }
    }

}
</script>

<style>
#app {
}
.title {
    text-align: center;
}

.body {
    background-color: #F5FAFF
}
</style>