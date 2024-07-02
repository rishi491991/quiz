<template>
  <div class="ctr">
    <Questions :questions="questions" :questions-answered="questionsAnswered" @answered="isAnswerCorrect"/>
    <Result v-if="questionsAnswered === questions.length" :correct-answered="correctAnswered"/>
    <button type="button" class="reset-btn" @click="resetAll">Reset</button>
</div>
</template>

<script>
import Questions from './components/Questions.vue';
import Result from './components/Result.vue';
export default {
    name:  'App',
    components: {
        Questions,
        Result,
    },
    data () {
      return {
    questions: [
        {
            q: 'What is 2 + 2?', 
            answers: [
                {
                    text: '4',
                    is_correct: true
                },
                {
                    text: '3',
                    is_correct: false 
                },
                {
                    text: 'Fish',
                    is_correct: false 
                },
                {
                    text: '5',
                    is_correct: false 
                }
            ] 
        },
        { 
            q: 'How many letters are in the word "Banana"?', 
            answers: [
                {
                    text: '5',
                    is_correct: false
                },
                {
                    text: '7',
                    is_correct: false 
                },
                {
                    text: '6',
                    is_correct: true 
                },
                {
                    text: '12',
                    is_correct: false 
                }
            ] 
        },
        { 
            q: 'Find the missing letter: C_ke', 
            answers: [
                {
                    text: 'e',
                    is_correct: false
                },
                {
                    text: 'a',
                    is_correct: true 
                },
                {
                    text: 'i',
                    is_correct: false 
                }
            ] 
        },
    ],
    results: [
        {
            min: 0,
            max: 2,
            title: "Try again!",
            desc: "Do a little more studying and you may succeed!"
        },
        {
            min: 3,
            max: 3,
            title: "Wow, you're a genius!",
            desc: "Studying has definitely paid off for you!"
        }
    ],
    questionsAnswered: 0,
    correctAnswered:0,
};
},
    methods: {
        isAnswerCorrect(isCorrect) {
            if(isCorrect){
                this.correctAnswered++;
            }
            this.questionsAnswered++;
        },
        resetAll(){
            this.questionsAnswered = 0;
            this.correctAnswered = 0;
        }
    }
    }
</script>
