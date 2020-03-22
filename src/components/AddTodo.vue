<template>
<div>
    <form @submit="addTodo">
        <input type="text" v-model="title" name="title">
        <button type="submit">
            <i class="fas fa-plus"></i>
        </button>
    </form>

    <p class="error-notification" v-if="display" :class="{display: display}">
        Type something...
    </p>

</div>
</template>

<script>
// import uuid from 'uuidv4'; **v4 of undefined hatası**

export default {
    name: 'AddTodo',
    data() {
        return {
            title: '',
            key: 6,
            display: false
        }
    },
    methods: {
        addTodo(e) {
            e.preventDefault();

            if (this.title != '') {
                
                this.display = false;

                const newTodoObj = {
                    id: this.key,
                    title: this.title,
                    completed: false
                }
                this.$emit('add-todo', newTodoObj);
                this.title = '';
                this.key++;
            } else {
                this.display = true
            }
        }
    }
}
</script>

<style scoped>

@import url('https://fonts.googleapis.com/css?family=Poppins&display=swap');

    form {
        margin-top: 30px;
        position: relative;
        width: 90%;
        margin-left: 10%;
    }
    input {
        width: 77.5%;
        border:none;
        border-bottom: 1px solid #4461d9;
        background: transparent;
        padding: 8px 0;
        font-family: 'Gochi Hand', cursive;
        font-size: 18px;
        opacity: .8;
        outline: none;        
    }

    button {
        background: transparent;
        padding: 10px 20px;
        margin-left: 10px;
        border: none;
        color: #4461d9;
        outline: none;
        cursor: pointer;
        font-size: 16px;
        border-radius: 4px;
        box-shadow: 2px 3px 5px 2px rgba(50, 50, 50, .25);
    }
    button:hover {
        transition-duration: .5s;
        background: #4461d9;
    }
    svg {        
        color: #4461d9;
    }
    button:hover svg {        
        color: white;
    }

    .error-notification {
        background: #4461d9;
        position: absolute;
        top: 0;
        left: 50%;
        transform: translateX(-50%);
        width:200px;
        margin: 0;
        height: 30px;
        font-size: 18px;
        text-align: center;
        border-radius: 2px;
        font-family: 'Poppins', sans-serif;
        color: white;
        box-shadow: 1px 5px 5px 1px rgba(0, 0, 150, .5);
        padding: 10px 30px;
    }
</style>
