<template>
  <div>
    <p>Completed Tasks: {{todos.filter(todo => {return todo.done === true}).length}}</p>
    <p>Pending Tasks: {{todos.filter(todo => {return todo.done === false}).length}}</p>
    <create-todo v-on:add-todo="addTodo"></create-todo>
    <todo  v-for="(todo, index) in todos" :key="index" v-bind:todo="todo" v-on:delete-todo="deleteTodo">
    </todo>
  </div>
</template>

<script type="text/javascript">
import Todo from '../Todo/Todo';
import CreateTodo from '../CreateTodo/CreateTodo';

    export default{
        props: ['todos'],
        components:{
            Todo,
            CreateTodo,
        },
        methods:{
            deleteTodo(todo){
               const todoIndex = this.todos.indexOf(todo);
            this.todos.splice(todoIndex, 1);
            },
            addTodo(newTodo){
                const title= newTodo.title;
                const project = newTodo.project;
                const done = newTodo.done
                this.todos.push(
                    newTodo);
                
            },
        },
    }
</script>
<style>
</style>