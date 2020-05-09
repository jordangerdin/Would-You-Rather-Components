<template>
    <div>
        <div id="card" class="card shadow m-2 p-2">
            <h2 class="card-text">{{ question }}</h2>
            <div class="card-body">
                <div class="btn-group btn-group-toggle" data-toggle="buttons">
                    <label class="btn btn-secondary">
                        <input 
                        type="radio" 
                        v-model="choice" 
                        v-bind:value="answer1" 
                        v-on:change="questionAnswered(choice)">
                        {{ answer1 }}
                    </label>
                    
                    <label class="btn btn-secondary">
                        <input 
                        type="radio" 
                        v-model="choice" 
                        v-bind:value="answer2" 
                        v-on:change="questionAnswered(choice)">
                        {{ answer2 }}
                    </label>
                </div>
            </div>
        </div>
    </div>    
</template>

<script>
    export default {
        name: 'WouldYouRatherQuestion',
        data() {        /* Data - for internal data that belongs to this component */
            return {
                choice: ''
            }
        },
        props: {        /* Props - for data passed in from parent component */
            id: Number,
            question: String,
            answer1: String,
            answer2: String,
            
        },
        methods: {
            questionAnswered(choice) {
                console.log(`Answer changed: ${choice}`)
                this.$emit('answer-changed', this.id, choice)
            }
        }
    }
</script>

<style>
#card{
    background-color: aliceblue;
}
</style>

