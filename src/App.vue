<template>
  <div id="app">
    <h1>List Todo Anda</h1>
    <div class="input-teks-bok">
      <input-teks-bok  @update-title="updateTitle"/>
    </div>
    <div class="list-todo-bok">
      <list-todo-bok :todos="todos" @delete-todo="deleteTodo" />>
    </div>
    
  </div>
</template>

<script>

import InputTeksBok from './components/InputTeksBok.vue'
import ListTodoBok from './components/ListTodoBok.vue'
export default {
  name: 'App',
  components: {
    'input-teks-bok': InputTeksBok,
    'list-todo-bok': ListTodoBok
  },
  data() {
      return {
          todos: [
              { id:1, title:'Mencuci Pakaian', accomplish: false },
              { id:2, title: 'Mengerjakan PR', accomplish: false },
          ],
          newTodo: ''
      }
  },
  methods: {
    updateTitle(title) {
      var newId = Math.random().toString(36).substr(2, 9)
      console.log(newId)
      this.newTodo = title
      this.todos.push({
        id: newId,
        title,
        accomplish: false
      })
    },
    deleteTodo(id) {
       this.todos = this.todos.filter(todo => todo.id !== id);
    }
  },
}
</script>

<style lang="scss">
#app {
  background-color: $info;
  min-height: 500px;
  font-family: Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  //this is where we use the variable
  color: $secondary;
  margin-top: 60px;
  margin-bottom:5px;

  h1 {
    font-weight:bold;
    color:$primary;
  }
}

.input-teks-box {
  padding-top: 10px;
}

</style>
