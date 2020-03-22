<template>
    <div >
        <p v-bind:class="{ 'completed': todo.completed}" v-on:click="markComplete"> - {{todo.title}} </p>
        <button class="delete-button" @click="$emit('delete-todo', todo.id)">
            <i class="far fa-trash-alt"></i>
        </button>
    </div>
</template>

<script src="https://kit.fontawesome.com/your-code-number.js"></script>

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
@import url('https://fonts.googleapis.com/css?family=Gochi+Hand&display=swap');

    .completed {
        text-decoration: line-through;
        transition-duration: .5s;
        opacity: .5;
    }
    p {
        display:inline-block;
        width:375px;
        opacity: .8;
        cursor: pointer;
    }
    p:hover {
        transition-duration: .5s;
        opacity: 1;
    }
    .delete-button {
        border: none;
        border-radius: 3px;
        background: transparent;
        box-shadow: 2px 3px 5px 2px rgba(50, 50, 50, .25);
        padding: 10px 15px;
        cursor: pointer;
    }
    .delete-button svg {
        font-size: 18px;
        opacity: .8;
    }
    .delete-button:hover {
        transition-duration: .25s;
        background: #eee;
    }
</style>