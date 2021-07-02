<template>
  <div class="to_do_list">
    <h1>Todo List</h1>
    <v-btn
      color="primary"
      elevation="2"
      @click="clearAll"
    >
      clear all
    </v-btn>
    <div v-if="todos ===  null">
      Loading...
    </div>
    <v-card
      v-else
      class="mx-auto"
      max-width="400"
      tile
    >
      <div v-if="todos.length === 0"> Nothing need to do </div>
      <v-list-item
        v-for="todo in todos"
        :key="todo.id"
      >
        <v-list-item-content>
          <v-list-item-title>{{ todo.content }}</v-list-item-title>
        </v-list-item-content>
        <v-btn @click="deleteTodo(todo)"> delete </v-btn>
      </v-list-item>
    </v-card>
  </div>
</template>

<script>

export default {
  name: 'TodoList',
  data: () => ({
    todos: null,
  }),
  mounted() {
    this.reloadTodo();
  },
  methods: {
    clearAll() {
      localStorage.removeItem('todos');
      this.reloadTodo();
    },
    deleteTodo(todo) {
      this.todos.splice(this.todos.indexOf(todo), 1);
      localStorage.setItem('todos', JSON.stringify(this.todos));
      this.reloadTodo();
    },
    reloadTodo() {
      this.todos = JSON.parse(localStorage.getItem('todos') || '[]');
    },

  },
};
</script>
