<template>
    <div>
        <link rel="stylesheet"
              href="https://cdn.jsdelivr.net/npm/bootstrap@4.5.3/dist/css/bootstrap.min.css"
              integrity="sha384-TX8t27EcRE3e/ihU7zmQxVncDAy5uIKz4rEkgIXeMed4M0jlfIDPvg6uqKI2xXr2"
              crossorigin="anonymous"
        >
        <div class="container">
            {{something}}
            <br>
            {{fullName}}
            <h1> Parent: {{carName}}</h1>
            <app-car :carName="carName" :carYear="carYear" @nameChanged="carName=$event"></app-car>
            <h2 :title="title">
                Наведи на меня курсор на пару секунд,
                чтобы увидеть динамически связанное значение title!
            </h2>
            <ol class="list-group col-3">
                <li class="list-group-item" v-for="(todo,index) in todos" :key="todo">{{index+1}}.{{todo.text}}</li>
            </ol>
            <br>
            <app-todo class="list-group col-3"
                      v-for="item in groceryList"
                      v-bind:todo="item"
                      :key="item.id"
            ></app-todo>

            <base-layout>
                <template v-slot:header>
                    <h1>Здесь мог быть заголовок страницы</h1>
                </template>


                <template v-slot:default="slotProps">
                    {{ slotProps.user.lastName }}
                    <p>Параграф для основного контента.</p>
                    <p>И ещё один.</p>
                </template>

                <template v-slot:footer>
                    <p>Некая контактная информация</p>
                </template>
            </base-layout>
        </div>
    </div>
</template>


<script>
    import Car from './components/car/car.vue'
    import Todo from './components/todo/todo.vue'
    import baseLayout from './components/layout/layout'


    export default {
        name: 'App',
        data() {
            return {
                firstName: 'Foo',
                lastName: 'Bar',
                carName: 'Car from parent',
                carYear: 2000,
                title: 'This is title ' + new Date().toLocaleString(),
                todos: [
                    {text: 'Изучить JavaScript'},
                    {text: 'Изучить Vue'},
                    {text: 'Создать что-нибудь классное'}
                ],
                groceryList: [
                    {id: 0, text: 'Овощи'},
                    {id: 1, text: 'Сыр'},
                    {id: 2, text: 'Что там ещё люди едят?'}
                ]
            };
        },
        components: {
            'app-car': Car,
            'app-todo': Todo,
            'base-layout': baseLayout

        },
        computed: {
            something() {
                console.log(this.$options)
                console.log(this.$root)
                console.log(this.$children)
                console.log(this.$listeners)
                return 'Done'
            },
            fullName: {
                get: function () {
                    return this.firstName + ' ' + this.lastName
                },
                set: function (newValue) {
                    const names = newValue.split(' ')
                    this.firstName = names[0]
                    this.lastName = names[names.length - 1]
                }
            }
        }
    }

</script>

