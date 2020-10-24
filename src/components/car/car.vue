<template>
    <div class="car">
        <h3>Name: {{carName}} \ {{reverse}} </h3>
        <h3>Year: {{carYear}}</h3>
        <div class="btn btn-success" @click="changeName">change</div>
    </div>
</template>

<script>
    export default {
        // props:['carName','carYear'],
        props: {
            'carName': {
                type: String,
                required: true,
                default: 'Default Name',
            },
            'carYear': Number
        },
        data() {
            return {}
        },
        methods: {
            changeName: function () {
                this.carName = '123'
                this.$emit('nameChanged', this.carName)
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
