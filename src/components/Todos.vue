<template>
    <div>
        <h1> Todo List </h1> 
        <ul>
            <li v-bind:key="todo.id" v-for="todo in todos">
                <Todo v-bind:todo="todo" v-on:delete-todo="$emit('delete-todo', todo.id)" />
            </li>
        </ul>

    </div>
</template>

<script>

import Todo from './Todo'; 

export default {
    name: 'Todos',
    components: {
        Todo
    },
    props: [
        "todos"
    ]
}
</script>

<style scoped>

    ul {
        list-style-type: none;
    }

    h1 {
        text-align: center;
        color: #4461d9;
    }
</style>