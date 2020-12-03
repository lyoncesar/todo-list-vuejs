<template>
  <div>
    <input type="checkbox" v-bind:id="id" v-bind:checked="isDone" />
    <label v-bind:for="id">{{label}}</label>
  </div>
</template>
<script>
  export default {
    name: 'ToDoItem',
    props: {
      id: {
        required: true,
        type: String
      },
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
        isDone: this.done
      };
    },
  };
</script>
<style>
  
</style>
