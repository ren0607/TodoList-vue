<template>
    <div>
        <v-app-bar dark color="indigo">
            <v-btn icon to="/"><v-icon>arrow_back</v-icon></v-btn>
            <v-toolbar-title class="white--text">
                家計簿
            </v-toolbar-title>
        </v-app-bar>
        <v-text-field v-model="newTodo" placeholder="Input here..."></v-text-field>
        <v-btn dark color="indigo" v-on:click="addTodo()" class="white--text">
            ADD
        </v-btn>
    </div>
</template>
<script>
    export default {
        data() {
            return {
                newTodo: ''
            }
        },
        methods: {
            addTodo() {
                if(this.newTodo === '') return;
                const todos = JSON.parse(localStorage.getItem('todos')) || [];
                todos.push(this.newTodo);
                localStorage.setItem('todos', JSON.stringify(todos));
                this.newTodo = '';
                this.$router.push('/');
            }
        }
    }
</script>
<style scoped>

</style>
