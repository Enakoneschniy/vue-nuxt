<template>
  <div class="todo-list-wrapper">
    <ul>
      <TodoItem
        v-for="todo of todos"
        :key="todo.id"
        :todo="todo"
        @edit="onEdit"
        @delete="onDelete"
      />
    </ul>
  </div>

</template>

<script>
  import TodoItem from "./TodoItem";

  export default {
    name: "TodoList",
    components: { TodoItem },
    props: {
      todos: {
        type: Array,
        required: true
      }
    },
    methods: {
      onDelete(id) {
        this.$emit('delete', id);
      },
      onEdit(data) {
        this.$emit('edit', data);
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
