<template>
  <div class="todo">
  <div>
    <form @submit.prevent="edit_form">
      <input name='todo_name' id='todo_name' v-model="todo_name" />
      <button name='edit_todo' id='edit_todo' :value='todo_id' > Edit </button>
    </form>  
    <button name='del_todo' id='del_todo' v-on:click="delete_todo()" > Delete </button>
  </div>
  </div>
</template>

<script>
export default {
  name: 'Todo',
  props: [
    'todo_name', 'todo_id'
  ],
  methods: {
    edit_form() {
      this.$emit('edit_todo', [this.todo_id, this.todo_name])
    },
    delete_todo() {
      this.$emit('delete_todo',this.todo_id)
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
