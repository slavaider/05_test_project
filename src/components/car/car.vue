<template>
    <div class="car">
        <h3>Name: {{carName}} \ {{reverse}} </h3>
        <h3>Year: {{carYear}}</h3>
        <div class="d-flex justify-content-between">
            <div class="btn btn-success" @click="changeName">change</div>
            <div class="btn btn-success" @click="changeFunc">Change from parent</div>
            <div class="btn btn-success" @click="update_counter">update_counter</div>
        </div>
    </div>
</template>

<script>
    import {EventEmitter} from "@/main";

    export default {
        // props:['carName','carYear'],
        props: {
            'carName': {
                type: String,
                required: true,
                default: 'Default Name',
            },
            'carYear': Number,
            'changeFunc': Function
        },
        data() {
            return {}
        },
        methods: {
            changeName: function () {
                this.carName = '123'
                this.$emit('nameChanged', this.carName)
            },
            update_counter() {
                // this.$emit('counterChanged', this.counter + 1)
                EventEmitter.$emit('counterChanged', 3)
            }
        },
        computed: {
            reverse: function () {
                return this.carName.split('').reverse().join('')
            }
        }
    };
</script>
<style scoped>
    .car {
        border: 1px solid black;
        margin: 10px;
        padding: 10px;
    }
</style>
