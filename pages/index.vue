<template>
  <section class="container">
    <CreateTodoForm @add="onAdd"/>
    <TodoList :todos="todos" @delete="onDelete" @edit="onEdit"/>
  </section>
</template>

<script>
  import TodoList from "../components/TodoList";
  import CreateTodoForm from "../components/CreateTodoForm";

  export default {
    components: { CreateTodoForm, TodoList },
    layout: 'home',
    data() {
      return {
        todos: []
      }
    },
    async asyncData({ $axios }) {

      return {
        todos: []
      }
    },
    head () {
      return {
        title: 'TODOS',
        meta: [
          // hid is used as unique identifier. Do not use `vmid` for it as it will not work
          { hid: 'description', name: 'description', content: 'My custom description' }
        ]
      }
    },
    async created() {

    },
    methods: {
      onDelete(id) {
        const obj = Object.assign({}, { a: 3, b: 2 }, { a: 1 });
        const index = this.todos.findIndex(item => item.id === id);
        this.todos.splice(index, 1);
      },
      onEdit(data) {
        this.todos = this.todos.map(todo => {
          if (todo.id === data.id) {
            todo.name = data.newName;
          }
          return todo;
        })
      },
      onAdd(todo) {
        this.todos.push(todo);
      }
    }
  }
</script>
