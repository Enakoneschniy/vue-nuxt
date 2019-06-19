<template>
  <li class="d-flex align-items-center justify-content-between mb-2">
    <b-form-checkbox v-if="!isEdit" :id="`checkbox-${todo.id}`" name="is_done">
      {{ todo.name }}
    </b-form-checkbox>
    <div v-else>
      <b-input
        id="inline-form-input-name"
        class="mr-sm-2"
        v-model="newName"
        name="name"
        placeholder="Todo Name"
      ></b-input>
      <b-form-invalid-feedback :state="errors.has('name')">
        {{ errors.first('name') }}
      </b-form-invalid-feedback>
    </div>
    <div>
      <b-button v-if="!isEdit" variant="info" size="sm" @click.prevent="onToggleEdit">Edit</b-button>
      <b-button v-else variant="success" size="sm" @click="onSave">Save</b-button>
      <b-button v-if="isEdit" variant="danger" size="sm" @click="onCancel">Cancel</b-button>
      <b-button variant="danger" v-if="!isEdit" size="sm" @click.prevent="onDelete(todo)">Delete</b-button>
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
    data() {
      return {
        newName: this.todo.name,
        isEdit: false
      }
    },
    methods: {
      onToggleEdit() {
        this.isEdit = !this.isEdit;
      },
      onSave() {
        this.onToggleEdit();
        this.$emit('edit', {
          newName: this.newName,
          id: this.todo.id
        });
        this.newName = this.todo.name;
      },
      onCancel() {
        this.onToggleEdit();
        this.newName = this.todo.name;
      },
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
