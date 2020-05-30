<template>
    <div id="app">
        <h1>The Super Quiz</h1>
        <component :is="cardComponent" :answer="correctAnswer">
            <template v-slot:question>
                <p>
                    What is {{ firstNumber }} {{ operationSymbol }}
                    {{ secondNumber }}?
                </p>
            </template>
        </component>
    </div>
</template>

<script>
import Question from './components/Question'
import Correct from './components/Correct'
import Wrong from './components/Wrong'
import TimesUp from './components/TimesUp'
export default {
    components: {
        Question,
        Correct,
        Wrong,
        TimesUp,
    },
    data() {
        return {
            cardComponent: 'Question',
            firstNumber: Math.floor(Math.random() * 80 + 20), // number between 20 and 100
            secondNumber: Math.floor(Math.random() * 50 + 10), // number between 10 and 60
            operationNumber: Math.floor(Math.random() * 4 + 1), // number between 1 and 4
        }
    },
    computed: {
        operationSymbol() {
            switch (this.operationNumber) {
                case 1:
                    return '+'
                case 2:
                    return '-'
                case 3:
                    return '*'
                case 4:
                    return '/'
            }
        },
        correctAnswer() {
            switch (this.operationSymbol) {
                case '+':
                    return this.firstNumber + this.secondNumber
                case '-':
                    return this.firstNumber - this.secondNumber
                case '*':
                    return this.firstNumber * this.secondNumber
                case '/':
                    return (this.firstNumber / this.secondNumber).toFixed(2)
            }
        },
    },
}
</script>

<style>
body {
    font-family: sans-serif;
    display: flex;
    justify-content: center;
    align-items: center;
    height: 90vh;
    margin: 0;
}
#app {
    max-width: 400px;
    width: 100%;
    padding: 0.5rem;
}
* {
    box-sizing: border-box;
}
*:focus {
    outline: none;
}
h1 {
    text-align: center;
}
.component-body {
    box-shadow: 0 4px 8px 0 rgba(0, 0, 0, 0.2), 0 6px 20px 0 rgba(0, 0, 0, 0.19);
    border-radius: 4px;
    padding: 0.75rem;
    width: 100%;
    font-weight: bold;
    font-size: 1.2rem;
    height: 10rem;
    color: white;
    display: flex;
    flex-direction: column;
    justify-content: space-between;
}
button {
    font-size: 1.2rem;
    font-weight: bold;
    border: none;
    background: inherit;
    cursor: pointer;
    color: white;
}
.message {
    text-align: center;
    margin: 0;
}
.header {
    font-size: 1.4rem;
    margin: 0;
}
</style>
