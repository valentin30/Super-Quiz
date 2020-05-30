<template>
    <div class="component-body">
        <p class="timer">9</p>
        <slot name="question"> </slot>
        <div class="answers">
            <button>{{ answer }}</button>
            <button>{{ answer }}</button>
            <button>{{ answer }}</button>
            <button>{{ answer }}</button>
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
    color: white;
    display: flex;
    flex-direction: column;
    justify-content: space-between;
}
p {
    text-align: center;
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
    color: white;
    margin: 1rem;
}
</style>
