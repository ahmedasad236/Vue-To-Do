<template>
  <ul class="todos">
    <list-item-vue
      v-for="todo in filteredTodos"
      :key="todo.todo"
      :getTodo="getTodo"
      :removeFromTodos="removeFromTodos"
      :todo="todo"
      :toggleCompleted="toggleCompleted"
    />
  </ul>
</template>

<script>
import ListItemVue from './ListItem.vue';

export default {
  name: 'TodoList',
  components: {
    ListItemVue
  },
  props: {
    todos: Array,
    showCurrentTodo: Boolean,
    showCompleted: Boolean,
    showUnCompleted: Boolean,
    getTodo: Function,
    removeFromTodos: Function,
    toggleCompleted: Function
  },
  computed: {
    filteredTodos() {
      if (this.showCompleted)
        return this.todos.filter((todo) => todo.completed);
      else if (this.showUnCompleted)
        return this.todos.filter((todo) => !todo.completed);
      else return this.todos;
    }
  },
  methods: {}
};
</script>

<style scoped>
.todos {
  list-style: none;
  display: flex;
  flex-direction: column;
  gap: 1rem;
  padding: 0;
}
</style>
