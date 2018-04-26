<template>
  <div id="app" class="container">
    <h1 class="text-center">Todo App</h1>
    <form @submit.prevent="addTodo()">
      <div class="form-group">
        <label for="newTodo">New Todo:</label>
        <input v-model="newTodo" type="text" class="form-control" id="newTodo" aria-describedby="newTodoHelp" placeholder="make a todo">
        <small id="newTodoHelp" class="form-text text-muted">Enter a new todo...</small>
      </div>
      <button type="submit" class="btn btn-primary">Add Todo</button>
    </form>
    <ul class="list-group mt-3">
      <li v-for="(todo, currentIndex) in todos" class="list-group-item">
        <button
          v-if="!todo.done"
          @click="markDone(todo)"
          type="button"
          class="btn btn-success">Completed</button>
        <button
        @click="removeTodo(currentIndex)"
        type="button"
        class="btn btn-danger ">Remove todo</button>
        <span v-bind:class="{
          isDone: todo.done
        }">{{todo.title}}</span>
      </li>
        
    </ul>
  </div>
</template>

<script>
export default {
  name: 'app',
  data () {
    return {
     newTodo: '', 
     todos: []
    }
  },
  methods: {
    addTodo() {
      this.todos.push({
        title: this.newTodo,
        done: false
      });
      this.newTodo = '';
    },
    markDone(todo) {
      todo.done = true;
    },
    removeTodo(index) {
      this.todos.splice(index, 1);
    }
  }
}
</script>

<style>
 .isDone {
   color: green;
   text-decoration: line-through;
 }
</style>
