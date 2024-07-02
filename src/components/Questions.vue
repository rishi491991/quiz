<template>
    <div class="questions-ctr">
        <div class="progress">
            <div class="bar" :style="{width:`${(questionsAnswered/questions.length)*100}%`}"></div>
            <div class="status">{{ questionsAnswered }} out of 3 questions answered</div>
            
        </div>
        <div class="single-question" v-for="(question, index) in questions">
            <div v-if="index === questionsAnswered">
            <div class="question" :key="question.q" >{{ question.q }}</div>
            <div class="answers">
                <div class="answer" v-for="answer in question.answers" :key="answer" @click="checkAnswer(answer.is_correct)">{{ answer.text }}</div>
            </div>
        </div>
        </div>
    </div>
</template>
<script>
export default {
    name: 'Questions',
    props: ['questions','questionsAnswered'],
    methods: {
        checkAnswer(isCorrect){
            this.$emit("answered",isCorrect)
        }
    }
}
</script>