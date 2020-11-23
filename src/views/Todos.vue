<template>
  <div>
    <h2>Todo application</h2>
    <hr/>
    <AddTodo @add-todo="addTodo"/>
    <hr/>
    <Loader v-if="loading"/>
    <TodoList 
        v-else-if="todos.length"
        v-bind:todos="todos" 
        @remove-todo="removeTodo"/>
    <p v-else>No todos!</p>        
    <p>
        <router-link to="/">Back to home</router-link>
    </p>
  </div>
</template>

<script>
 
import TodoList from '@/components/TodoList';
import AddTodo from '@/components/AddTodo';
import Loader from '@/components/Loader';

export default {
  name: 'App',
  data() {
    return {
      todos: [],
      loading: true
    }
  },
  components: {
    TodoList, AddTodo, Loader
  },
  mounted() {
    fetch('https://jsonplaceholder.typicode.com/todos?_limit=3')
    .then(response => response.json())
    .then(json => {

        setTimeout(() => {
            this.todos = json;
            this.loading = false;
        }, 1000);


    });
  },
  methods: {
    removeTodo(id) {
      this.todos = this.todos.filter(x => x.id !== id);
    },

    addTodo(title) {
      if(!title || title.length === 0)
        return;      
      this.todos.push({id: this.todos.length + 1, title: title, completed: false });
    }

  }
}
</script>