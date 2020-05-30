<template>
    <div class="component-body">
        <p class="timer">9</p>
        <slot name="question"> </slot>
        <div class="answers">
            <button>1</button>
            <button>{{ answer }}</button>
            <button>1</button>
            <button>1</button>
        </div>
    </div>
</template>

<script>
export default {
    props: ['answer'],
    data() {
        return {}
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
