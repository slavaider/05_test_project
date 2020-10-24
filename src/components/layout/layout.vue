<template>
    <div class="container">
        <header class="text-center">
            <slot name="header"></slot>  <!-- Мы хотим отобразить контент заголовка здесь -->
        </header>
        <main>
            <slot v-bind:user="user">
                {{ user.firstName }}
            </slot> <!-- Мы хотим отобразить основной контент здесь -->
        </main>
        <footer>
            <slot name="footer"></slot> <!-- Мы хотим отобразить контент подвала здесь -->
        </footer>
    </div>
</template>

<script>
    export default {
        props: {},
        data() {
            return {
                user: {firstName: 'lol', lastName: '123'},
            }
        }
    };
</script>
