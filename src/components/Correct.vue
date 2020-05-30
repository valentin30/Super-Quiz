<template>
    <div class="component-body">
        <p class="header">Correct!</p>
        <p class="message">Yes! {{ answer }} is the answer.</p>
        <button @click="$emit('changeComponent', 'Question')">Next</button>
    </div>
</template>

<script>
export default {
    props: ['answer'],
}
</script>

<style scoped>
.component-body {
    background-color: rgb(156, 224, 156);
    padding: 1.5rem 1.2rem 1rem;
}
button {
    align-self: flex-end;
}
</style>
