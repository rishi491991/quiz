<template>
    <div class="result">
        <div class="title">Your Result: {{ correctAnswered }} correct answers</div>
        <div class="desc" v-if="correctAnswered === 3">
            You're a genius.
        </div>
        <div class="desc" v-if="correctAnswered < 3">
            You gotta practice more.
        </div>
    </div>
</template>
<script>
export default  {
    name: 'Result',
    props:['correctAnswered']
}
</script>