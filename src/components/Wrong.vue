<template>
    <div class="component-body">
        <p class="header">Wrong!</p>
        <p class="message">No! {{ answer }} is the answer.</p>
        <button>Try Again</button>
    </div>
</template>

<script>
export default {
    props: ['answer'],
}
</script>

<style scoped>
.component-body {
    background-color: tomato;
    padding: 1.5rem 1.2rem 1rem;
}
button {
    align-self: flex-end;
}
</style>
