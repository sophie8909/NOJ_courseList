<template>
  <div class="home">
    <h1>Home page</h1>
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
