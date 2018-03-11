<template>
  <div>
    <!-- JavaScript expressions in Vue are enclosed in double curly brackets. -->
    <p>Completed Tasks: {{items.filter(item => {return item.done === true}).length}}</p>
    <p>Pending Tasks: {{items.filter(item => {return item.done === false}).length}}</p>
    <todo v-on:delete-todo="deleteTodo" v-on:complete-todo="conpleteTodo" v-for="item in items" :key="item.name" v-bind:todo="item"/>
  </div>
</template>

<script type="text/javascript">
import Todo from "./Todo";

export default {
  props: ["items"],
  components: {
    Todo,
  },
  methods: {
    deleteTodo(todo) {
      const todoIndex = this.items.indexOf(todo);
      this.items.splice(todoIndex, 1);
    },
    completeTodo() {
      const todoIndex = this.items.indexOf(todo);
      this.items[todoIndex].done = true;
    },
  },
};
</script>

<style>

</style>
