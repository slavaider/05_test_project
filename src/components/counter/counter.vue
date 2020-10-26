<template>
    <div class="counter">
        Counter: {{counter}}
    </div>
</template>

<script>
    import {EventEmitter} from "@/main";

    export default {
        data() {
            return {
                counter: 0
            }
        },
        created() {
            EventEmitter.$on('counterChanged', (num) => {
                this.counter += num
            })
        }
    };
</script>
