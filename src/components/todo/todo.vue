<template>
        <div class="list-group-item">{{todo.id+1}}.{{ todo.text }}</div>
</template>

<script>
    export default {
        props: ['todo']
    };
</script>
