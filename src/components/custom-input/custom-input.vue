<template>
    <div class="custom-input">
        <label>
            <input
                    v-bind:value="value"
                    v-on:input="$emit('input', $event.target.value)"
            >
        </label>
    </div>
</template>

<script>
    export default {
        props: ['value'],
    };
</script>
