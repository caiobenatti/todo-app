<template>
<h1>Todo App</h1>
<form @submit.prevent="addNewTodo">
    <!-- the .prevent prevents it from refreshing the page -->
    <label> New Todo</label>
    <input name="newTodo" />
    <button>Add new Todo</button>
</form>
</template>

<script>
export default {
    setup() {
        function addNewTodo() {}
        return {
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
