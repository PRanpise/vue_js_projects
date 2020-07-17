<template>
  <div class='ui centered card'>
    <!-- <div :key="todo.id"  -->
     <div v-bind:key="todo.id" v-for="todo in todos">
      <TodoItem v-bind:todo="todo" />
    </div> 
  </div>
</template>
<script>
import TodoItem from './TodoItem';

export default {
  name: "Todos",
  components: {
    TodoItem,
  },
  props: ["todos"],

  methods: {
   
  },
};
</script>