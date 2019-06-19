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
    data() {
      return {
        todos: []
      }
    },
    methods: {
      onDelete(id) {
        const index = this.todos.findIndex(item => item.id === id);
        this.todos.splice(index, 1);
      },
      onEdit(data) {
        this.todos = this.todos.map(todo => {
          if(todo.id === data.id) {
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
