<template>
<h1>Todo App</h1>
<form @submit.prevent="addNewTodo">
    <!-- the .prevent prevents it from refreshing the page -->
    <label> New Todo</label>
    <input v-model="newTodo" name="newTodo" />
    <!-- v-model binds whats inside the box to the function setup -->
    <button>Add new Todo</button>
</form>
<h2>{{ newTodo }}</h2>
</template>

<script>
import {
    ref
} from "vue"; //remember to put inside the script tag, this is the helper to bind the ref to the v-model;

export default {
    setup() {
        const newTodo = ref("");
        const todos = ref([]); //creates an reactive array

        function addNewTodo() {
            console.log(newTodo.value);
        }
        return {
            todos,
            newTodo,
            addNewTodo,
        };
    },
};
</script>

<style>
#app {
    font-family: sans-serif;
    -webkit-font-smoothing: antialiased;
    -moz-osx-font-smoothing: grayscale;
    text-align: center;
    color: #2c3e50;
    margin-top: 60px;
    padding-top: 1em;
    padding-bottom: 1em;
    font-size: 2em;
    width: 80%;
    margin: 0 auto;
}
</style>
