<template>
    <div class="component-body">
        <p class="header">Times Up!</p>
        <p class="message">By the way {{ answer }} is the answer.</p>
        <button @click="$emit('changeComponent', 'Question')">Try Again</button>
    </div>
</template>

<script>
export default {
    props: ['answer'],
}
</script>

<style scoped>
.component-body {
    background-color: lightsalmon;
    padding: 1.5rem 1.2rem 1rem;
}
button {
    align-self: flex-end;
}
</style>
