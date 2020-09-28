<template>
<h1>Todo App</h1>
<form @submit.prevent="addNewTodo">
    <!-- the .prevent prevents it from refreshing the page -->
    <label> New Todo</label>
    <input v-model="newTodo" name="newTodo" />
    <!-- v-model binds whats inside the box to the function setup -->
    <button>Add new Todo</button>
</form>
<ul>
    <li v-for="(todo, index) in todos" v-bind:key="todo.id" class="todo">
        <!-- binds the key to the id on the addNewTodo function, and creates a loop to add a new h3/list item every time we add a new todo, then add the index as a way to remove the todo later -->
        <h3 :class="{ done: todo.done }" @click="toggleDone(todo)">
            {{ todo.content }}
        </h3>
        <button @click="removeTodo(index)">Remove ToDo</button>
    </li>
</ul>
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
            todos.value.push({
                id: Date.now(),
                done: false,
                content: newTodo.value,
            });
            newTodo.value = "";
        }

        function toggleDone(todo) {
            todo.done = !todo.done;
        }

        function removeTodo(index) {
            todos.value.splice(index, 1);
        }

        return {
            todos,
            newTodo,
            addNewTodo,
            toggleDone,
            removeTodo,
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

input,
textarea,
button,
p,
div,
section,
article,
select {
    display: block;
    width: 100%;
    font-family: sans-serif;
    font-size: 1em;
    margin: 0.5em;
}

.todo {
    cursor: pointer;
}

.done {
    text-decoration: line-through;
}
</style>
