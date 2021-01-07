<template>
  <div class="todos">
    <p> {{msg}} </p>
    <div v-for="todo in todoItems"
       :key="todo.id">
        
       <Todo @delete_todo="delete_todo" @edit_todo="edit_form" v-bind:todo_name="todo.name" v-bind:todo_id="todo.id"></Todo>
    </div>
    <div>
      <form v-on:submit.prevent="add_todo">
        <input name='new_todo' id='new_todo' v-model='new_todo' />
        <button name='add_todo' id='add_todo' type=submit>Add</button>
      </form>
    </div>
  </div>
</template>

<script>
import Todo from '../components/todo.vue'

export default {
  name: 'Todos',
  components: {
    Todo
  },
  data: function() {
    return { new_todo: "" } 
  },
  props: [
    'todoItems', 'msg'
  ],
  methods: {
    add_todo() {
      this.$emit('add_todo_child',this.new_todo)
    },
    edit_form(edit_array) {
      this.$emit('edit_form',edit_array)
    },
    delete_todo(del_id) {
      this.$emit('delete_todo',del_id)
    }
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
h3 {
  margin: 40px 0 0;
}
ul {
  list-style-type: none;
  padding: 0;
}
li {
  display: inline-block;
  margin: 0 10px;
}
a {
  color: #42b983;
}
</style>
