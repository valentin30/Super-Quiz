<template>
    <div class="component-body">
        <p class="timer">{{ this.timer }}</p>
        <slot name="question"> </slot>
        <div class="answers">
            <button>1</button>
            <button @click="$emit('changeComponent', 'Correct')">
                {{ answer }}
            </button>
            <button>1</button>
            <button>1</button>
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
    justify-content: center;
}
button {
    margin: 1rem;
}
</style>
