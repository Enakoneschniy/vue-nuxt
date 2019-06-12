<template>
  <li class="d-flex align-items-center justify-content-between mb-2">
    <b-form-checkbox id="checkbox-1" name="checkbox-1">
      {{ todo.name }}
    </b-form-checkbox>
    <div>
      <b-button variant="info" size="sm">Edit</b-button>
      <b-button variant="danger" size="sm" @click.prevent="onDelete(todo)">Delete</b-button>
    </div>

  </li>
</template>

<script>
  export default {
    name: "TodoItem",
    props: {
      todo: {
        type: Object,
        required: true
      }
    },
    methods: {
      onDelete(todo) {
        if(confirm(`Delete "${todo.name}"?`)) {
          this.$emit('delete', todo.id);
        }
      }
    }
  }
</script>

<style scoped>

</style>
