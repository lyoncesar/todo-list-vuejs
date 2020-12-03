<template>
  <div>
    <input type="checkbox" v-bind:id="id" v-bind:checked="isDone" />
    <label v-bind:for="id">{{label}}</label>
  </div>
</template>
<script>
  import uniqueId from 'lodash.uniqueid';
  export default {
    name: 'ToDoItem',
    props: {
      label: {
        required: true,
        type: String
      },
      done: {
        default: false,
        type: Boolean
      }
    },
    data() {
      return {
        id: uniqueId('todo-'),
        isDone: this.done
      };
    },
  };
</script>
<style>
  
</style>
