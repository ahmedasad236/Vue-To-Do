<template>
  <div class="container">
    <HeaderVue />
    <div class="display">
      <TodosListVue
        :getTodo="getTodo"
        :removeFromTodos="removeFromTodos"
        :showCompleted="showCompleted"
        :showCurrentTodo="showCurrentTodo"
        :showUnCompleted="showUnCompleted"
        :todos="todos"
        :toggleCompleted="toggleCompleted"
      />
      <NewTodoVue
        :addToTodo="addToTodo"
        :currentTodo="currentTodo"
        :onChangeCurrentTodo="onChangeCurrentTodo"
        :showCurrentTodo="showCurrentTodo"
      />
      <ActionBoxVue
        :showAllTodosHandler="showAllTodosHandler"
        :showCompletedTodosHandler="showCompletedTodosHandler"
        :showUnCompletedTodosHandler="showUnCompletedTodosHandler"
        :showCompleted="showCompleted"
        :showTodo="showTodo"
        :todosLength="todos.length"
        :showUnCompleted="showUnCompleted"
      />
    </div>
  </div>
</template>

<script>
import ActionBoxVue from './components/ActionBox.vue';
import HeaderVue from './components/Header.vue';
import NewTodoVue from './components/NewTodo.vue';
import TodosListVue from './components/TodosList.vue';

export default {
  name: 'App',

  components: {
    ActionBoxVue,
    TodosListVue,
    HeaderVue,
    NewTodoVue
  },

  data() {
    return {
      todos: [],
      currentTodo: '',
      showCurrentTodo: false,
      showCompleted: false,
      showUnCompleted: false
    };
  },

  methods: {
    removeFromTodos(todo) {
      this.todos = this.todos.filter((item) => item.todo != todo.todo);
    },

    getTodo(todo) {
      return this.todos.find((item) => item.todo === todo.todo);
    },

    toggleCompleted(todo) {
      const item = this.todos.find((item) => item.todo === todo.todo);
      item.completed = !item.completed;
    },

    onChangeCurrentTodo(event) {
      this.currentTodo = event.target.value;
    },

    addToTodo(todo) {
      if (!this.currentTodo) return;

      if (!this.todos.find((item) => item.todo === todo))
        this.todos.push({ todo, completed: false });
      this.currentTodo = '';
      this.showCurrentTodo = false;
    },

    showTodo() {
      this.showCurrentTodo = true;
    },
    showAllTodosHandler() {
      this.showCompleted = false;
      this.showUnCompleted = false;
    },
    showCompletedTodosHandler() {
      this.showCompleted = true;
      this.showUnCompleted = false;
    },
    showUnCompletedTodosHandler() {
      this.showCompleted = false;
      this.showUnCompleted = true;
    }
  }
};
</script>

<style>
.container {
  display: flex;
  flex-direction: column;
  background-color: #2c2e2f;
  color: aliceblue;
  padding: 5rem;
  gap: 2;
  height: 100vh;
  font-size: 1.2rem;
}

.display {
  display: flex;
  flex-direction: column;
}
</style>
