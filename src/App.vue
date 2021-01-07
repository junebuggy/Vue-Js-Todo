<template>
  <div id="app">
    <Todos v-bind:todoItems="todo_Items" v-bind:msg="my_msg" @add_todo_child="add_todo" @edit_form="edit_todo" @delete_todo="delete_todo"/>
  </div>
</template>

<script>
import Todos from './components/todos.vue'

export default {
  name: 'app',
  components: {
    Todos
  },
  data: function(){
    return {
      todo_Items: [
        { id: 1, name: 'do home work' },
        { id: 2, name: 'do house work' }
      ],
      my_msg: 'here we go ha ha ha'
    }
  },
  methods: {
    add_todo: function(newTodo) {
      var count = this.todo_Items.count
      this.todo_Items.push({id: count+1, name: newTodo})
    },
    edit_todo(edit_info) {
      var key = this.find_key("id", edit_info[0]);
      this.todo_Items[key].name = edit_info[1]
    },
    delete_todo(del_info) {
      var key = this.find_key("id", del_info);
      this.todo_Items.splice(key,1)
    },
    find_key(key, value) {
      for(var i = 0; i < this.todo_Items.length; i++)
      {
        if (this.todo_Items[i][key] == value) {
          return i;
        }
      }
      return null;
    }
  }
  
}
</script>

<style>
#app {
  font-family: 'Avenir', Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
