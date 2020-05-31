<template>
    <div class="component-body">
        <p class="timer">{{ this.timer }}</p>
        <slot name="question"> </slot>
        <div class="answers">
            <button
                v-for="(answer, index) in answers"
                :key="index"
                @click="submitAnswer(answer)"
            >
                {{ answer }}
            </button>
        </div>
    </div>
</template>

<script>
export default {
    props: ['answer'],
    data() {
        return {
            timer: 9,
            interval: null,
        }
    },
    methods: {
        startTimer() {
            this.timer = 9
            this.interval = setInterval(() => {
                if (!this.timer) {
                    this.$emit('changeComponent', 'TimesUp')
                }
                this.timer -= 1
            }, 1000)
        },
        submitAnswer(answer) {
            if (this.answer === answer) {
                this.$emit('changeComponent', 'Correct')
            } else {
                this.$emit('changeComponent', 'Wrong')
            }
        },
    },
    computed: {
        answers() {
            const correctAnswerIndex = Math.floor(Math.random() * 4)
            const answers = []
            for (let i = 0; i < 4; i++) {
                answers.push(
                    Math.floor(Math.random() * this.answer) +
                        Math.floor(
                            Math.random() *
                                (Math.random() + Math.random()) *
                                this.answer
                        )
                )
            }
            answers[correctAnswerIndex] = this.answer
            return answers
        },
    },
    mounted() {
        this.startTimer()
    },
    beforeDestroy() {
        clearInterval(this.interval)
    },
}
</script>

<style scoped>
.component-body {
    background-color: lightskyblue;
}
p {
    text-align: center;
    font-size: 1.3rem;
    margin: 0;
}
.timer {
    margin: 0;
    padding: 0;
    position: relative;
    text-align: end;
}
.answers {
    display: flex;
    flex-wrap: wrap;
    justify-content: space-evenly;
    margin-bottom: 1rem;
    width: 100%;
    align-self: center;
}
</style>
