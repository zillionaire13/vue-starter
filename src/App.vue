<script >
import TodoList from './components/Todo.vue'
import uniqueId from 'lodash.uniqueid'
import ToDoForm from './components/ToDoForm.vue'

export default {
  name: 'app',
  components: {
    TodoList,
    ToDoForm
  },
  data() {
    TodoList
    return {
      TodoItems: [
        {id: uniqueId('todo-'), label: 'Assess', done: false },
        {id: uniqueId('todo-'), label: 'Improvise', done: true },
        {id: uniqueId('todo-'), label: 'Adapt', done: false },
        {id: uniqueId('todo-'), label: 'Test', done: false },
        {id: uniqueId('todo-'), label: 'Overcome', done: false },
      ]
    }
  },
  methods: {
    addTodo(toDoLabel){
      this.TodoItems.push({id: uniqueId('todo-'), label:toDoLabel, done: false})
    }
  }
}
</script>

<template>
  <h1>To-Do List</h1>
  <div class="container">
    <to-do-form @todo-added="addTodo"></to-do-form>
    <ul class="list">
      <li v-for="item in TodoItems" :key="item.id"> 
        <todo-list :label="item.label" :done="item.done" :id="item.id"></todo-list>
      </li>
    </ul>
  </div>
</template>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
.list{
  list-style: none;
}
</style>
