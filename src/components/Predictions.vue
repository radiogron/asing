<template>
    <div
        class="predictions">
        <Asing
            :messages="currentAnswer"
            v-on:asingBellyClick="makePrediction"></Asing>

        <h1
            class="predictions__title">
            Предсказатель будущего «Асинг»</h1>
        <p
            class="predictions__description">
            Задай в уме вопрос, а потом нажми ему на пузико, чтобы получить ответ. Он может вас удивить.</p>
    </div>
</template>

<script>
import Asing from './Asing.vue'

export default {
    name: 'Predictions',
    data() {
      return{
        answers: [
            {
                position: 'left:50%;top:0;',
                message: 'Да'
            },
            {
                position: 'left:50%;top:0;',
                message: 'Нет'
            },
            {
                position: 'left:50%;top:0;',
                message: 'Нашел кого спросить'
            },
            {
                position: 'left:50%;top:0;',
                message: 'Может быть'
            },
            {
                position: 'left:50%;top:0;',
                message: 'Скорее нет, чем да'
            },
            {
                position: 'left:50%;top:0;',
                message: 'Печень это унисекс'
            },
            {
                position: 'left:50%;top:0;',
                message: 'Суслики! Они ебутся 2 секунды&nbsp;— я засекал!'
            }
        ],
        answerTimeout: null,
        answerStartPosition: -1
      }
    },
    created() {
        this.arrayAddID(this.answers);
    },
    methods: {
        makePrediction() {
            
            this.answerStartPosition = -1;
            clearTimeout(this.answer_timeout);

            this.answerStartPosition = Math.floor(Math.random() * Math.floor(this.answers.length));

            let time = this.currentAnswer[0].message.length * 300;
            if(time < 4000) time = 4000;
            this.answer_timeout = setTimeout(() => {
                this.answerStartPosition = -1;
                clearTimeout(this.answer_timeout);
            }, time)
        },
        arrayAddID(array) {
            array.map((item, index) => {
                item.id = index;
            })
        }
    },
    computed: {
        currentAnswer() {
            return this.answers.slice(this.answerStartPosition, this.answerStartPosition + 1)
        }
    },
    components: {
        Asing,
    }
}
</script>

<style lang="sass" scoped>

.predictions
    display: flex
    flex:
        direction: column
    align-items: center
    justify-content: center
    
    background-image: url('../assets/images/background-paper.jpg')
    min-height: 100vh
    padding:
        top: 40px
        bottom: 40px
    
    text-align: center
    // Elems
    .predictions__title
        font:
            size: 30px
            family: Arial, sans-serif
        margin:
            bottom: 0
    .predictions__description
        font:
            size: 18px
            family: Arial, sans-serif
        max-width: 60ch
</style>
