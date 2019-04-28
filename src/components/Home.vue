<template>
  <div class="home container center">
    <h1>Todo List</h1>
    <form @submit.prevent="addTodo">
      <label for="todo">Add a new Todo</label>
      <input type="text" v-model="todo">
    </form>
    <ol>
      <div class="row" v-for="(todo, index) in todos" :key="index">
        <div class="col m6"><li>{{ todo }}</li></div>
        <div class="col m3"><i class="material-icons" @click="deleteTodo(todo)">close</i></div>
        <div class="col m3"><i class="material-icons" @click="editTodo(todo)">edit</i></div>
      </div>
      <!-- <li v-for="(todo, index) in todos" :key="index">
        <span>{{ todo }}</span>
      </li> -->
    </ol>
  </div>
</template>

<script>
export default { 
  name: 'Home',
  data () {
    return {
      todos: [],
      todo: null
    }
  },
  methods: {
    addTodo () {
      if(this.todo){ 
        this.todos.push(this.todo)
        this.todo = ''
      } 
    },
    deleteTodo (todoToDelete) {
      this.todos = this.todos.filter(todo => {
        return todoToDelete != todo
      })
    },
    editTodo () {
      console.log('it works!')
    }
  }
}
</script>

<style>
.home{ 
  max-width: 500px;
}
</style>
