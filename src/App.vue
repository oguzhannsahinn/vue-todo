<template>
  <div id="app">

    <Todos v-bind:todos="todos" v-on:delete-todo="deleteTodo" />    
    <AddTodo v-on:add-todo="addTodo" />

  </div>
</template>

<script>
import Todos from './components/Todos';
import AddTodo from './components/AddTodo';

export default {
  name: 'app',
  components: {
    Todos,
    AddTodo
  },
  data() {
    return {
      todos:[
        {
          id: 1,
          title: 'Go workout',
          completed: false
        },
        {
          id: 2,
          title: 'Do laundry',
          completed: false
        },
        {
          id: 3,
          title: 'Cook food',
          completed: false
        },
        {
          id: 4,
          title: 'Clean up room',
          completed: false
        },
        {
          id: 5,
          title: 'Finish work',
          completed: false
        }
      ]
    }
  },
  methods: {
    addTodo(newTodoObj) {
      this.todos = [...this.todos, newTodoObj];
    },
    deleteTodo(todoId) {
      this.todos = this.todos.filter(todo => todo.id != todoId);
    }
  }
}
</script>

<style> 
@import url('https://fonts.googleapis.com/css?family=Poppins&display=swap');
@import url('https://fonts.googleapis.com/css?family=Gochi+Hand|Montserrat&display=swap');

  #app{
    width:500px;
    font-family: 'Gochi Hand', cursive;
    font-size: 22px;
    height:auto;
    margin: auto;
    box-shadow: 2px 5px 25px 2px rgba(50, 50, 50, .25);
    margin-top: 100px;
    padding: 30px;
    border-radius: 4px;
  }

  #app h1 {
    text-align: center;
  }
</style>
