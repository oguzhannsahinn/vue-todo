<template>
    <div >
        <p v-bind:class="{ 'completed': todo.completed}" v-on:click="markComplete"> {{todo.title}} </p>
         <button @click="$emit('delete-todo', todo.id)">Delete</button>
    </div>
</template>

<script>
export default {
    name: 'Todo',
    props: [
        "todo"
    ],
    methods: {
        markComplete() {
            this.todo.completed = !this.todo.completed;
        }
    }
}
</script>

<style scoped>
    .completed {
        text-decoration: line-through;
    }
    p {
        display:inline-block;
        width:400px;
    }
</style>