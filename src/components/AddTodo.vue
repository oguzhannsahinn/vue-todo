<template>
<div>
    <form @submit="addTodo">
        <input type="text" v-model="title" name="title">
        <button type="submit">Add</button>
    </form>
</div>
</template>

<script>
// import uuid from 'uuidv4';

export default {
    name: 'AddTodo',
    data() {
        return {
            title: '',
            key: 6
        }
    },
    methods: {
        addTodo(e) {
            e.preventDefault();
            if (this.title != '') {

                const newTodoObj = {
                    id: this.key,
                    title: this.title,
                    completed: false
                }
                this.$emit('add-todo', newTodoObj);
                this.title = '';
                this.key++;
            } else {
                alert('type something..!')
            }
        }
    }
}
</script>

<style scoped>
</style>
