<template>
  <div class="todo-list-wrapper">
    <b-form inline class="mb-3" @submit.prevent="onAddTodo">
      <b-input
        id="inline-form-input-name"
        class="mr-sm-2"
        v-model="newTodoName"
        placeholder="Todo Name"
      ></b-input>
      <b-button type="submit" variant="primary">Add</b-button>
    </b-form>
    <ul>
      <TodoItem
        v-for="todo of todos"
        :key="todo.id"
        :todo="todo"
        @delete="onDelete"
      />
    </ul>
  </div>

</template>

<script>
  function generateId() {
    return new Date().getTime();
  }

  import TodoItem from "./TodoItem";

  export default {
    name: "TodoList",
    components: { TodoItem },
    data() {
      return {
        newTodoName: '',
        todos: []
      }
    },
    methods: {
      onAddTodo() {
        this.todos.push({
          name: this.newTodoName,
          isDone: false,
          id: generateId()
        });
        this.newTodoName = '';
      },
      onDelete(id) {
        const index = this.todos.findIndex(item => item.id === id);
        this.todos.splice(index, 1);
      }
    }
  }
</script>

<style scoped lang="sass">
  .todo-list-wrapper
    width: 30%
    margin: 30px auto

    ul
      list-style: none
      margin: 0
      padding: 0

</style>
