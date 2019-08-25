<template>
  <div id="app">
    <div class="todo-wrapper">
      <app-header></app-header>
      <todo-input v-on:todo:add="addTodo"></todo-input>
      <todo-item v-for="todo in todos"
                 v-bind:todo="todo"
                 v-on:todo:remove="removeTodo"
                 :key="todo.id"></todo-item>

    </div>
  </div>
</template>

<script>
  import  AppHeader from './components/AppHeader'
  import  TodoInput from './components/TodoInput'
  import  TodoItem from './components/TodoItem'


  export default {
    name: 'app',
    components: {
      AppHeader,TodoInput,TodoItem
    },
    data(){
      return {
        todos:[
          {id: 0,text: "Make dinner tonight!"},
          {id: 1,text: "Fold the laundry."},
          {id: 2,text: "learn to make a Vue app!"},

        ],
        nextId: 3,


      }
    },
    methods:{
      addTodo(text){
        this.todos.push({id:this.nextId,text:text})
        this.nextId++

      },
      removeTodo(id){
        let todos = this.todos;
        this.todos = todos.filter((todo)=>todo.id != id)

      }
    }
  }
</script>

<style>
  #app{
    font-family: 'Avenir',Helvetica,Arial,sans-serif;
    -webkit-font-smoothing: antialiased;
    -moz-osx-font-smoothing: grayscale;
    text-align: center;
    color: #2c3e50;
    margin-top: 60px;
  }
  .todo-wrapper{
    margin: 20px auto 20px auto;
    width: 500px;
    min-height: 600px;
    border: 5px solid rgba(73,204,249,1.0);
    padding: 20px;
  }
</style>
