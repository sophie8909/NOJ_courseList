<template>
  <div class="home">
    <h1>Home page</h1>
    <v-text-field
      label="Todo"
      outlined
      v-model="newTodo"
    ></v-text-field>
    <v-btn @click="submit">
      Add
    </v-btn>
    <v-snackbar
      v-model="snackbar"
      :timeout="timeout"
    >
      {{ text }}
      <template v-slot:action="{ attrs }">
        <v-btn
          color="blue"
          text
          v-bind="attrs"
          @click="snackbar = false"
        >
          Close
        </v-btn>
      </template>
    </v-snackbar>
  </div>
</template>

<script>

export default {
  name: 'Home',
  data: () => ({
    newTodo: '',
    snackbar: false,
    text: 'Nothing created',
    timeout: 200000000,
  }),
  function: {
    isNull(str) {
      const regu = '^[ ] $';
      const re = new RegExp(regu);
      if (str === '') return true;
      return re.test(str);
    },
  },
  methods: {
    isNull(str) {
      if (str === '') return true;
      const regu = '^[ ] $';
      const re = new RegExp(regu);
      return re.test(str);
    },
    submit() {
      const todos = JSON.parse(localStorage.getItem('todos') || '[]');
      const newTodoItem = {
        id: todos.length + 1,
        content: this.newTodo,
      };
      if (this.isNull(this.newTodo) === true) {
        this.text = 'Content cannot be empty.';
      } else {
        this.text = `${this.newTodo} is created.`;
        localStorage.setItem('todos', JSON.stringify([...todos, newTodoItem]));
      }
      this.newTodo = '';
      this.snackbar = true;
    },
  },
};
</script>
