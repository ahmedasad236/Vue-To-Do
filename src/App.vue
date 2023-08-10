<template>
  <div class="container">
    <h1 class="heading">Todos</h1>
    <div class="display">
      <ul class="todos">
        <li
          v-for="todo in todos"
          :key="todo"
        >
          <div>
            <input type="checkbox" />
            <sapn>{{ todo }}</sapn>
            <button @click="removeFromTodos(todo)">&times;</button>
          </div>
        </li>
      </ul>
      <div v-if="showCurrentTodo">
        <input
          v-model="currentTodo"
          id="enter-todo"
          placeholder="Enter todo..."
        />
        <button @click="addToTodo(currentTodo)">&#x2713;</button>
      </div>
      <button @click="showTodo()">+</button>
    </div>
  </div>
</template>

<script>
export default {
  name: 'App',
  data() {
    return {
      todos: ['hello'],
      currentTodo: '',
      showCurrentTodo: false
    };
  },
  methods: {
    removeFromTodos(todo) {
      this.todos = this.todos.filter((item) => item != todo);
    },

    addToTodo(todo) {
      if (!this.currentTodo) return;

      this.todos.push(todo);
      this.currentTodo = '';
      this.showCurrentTodo = false;
    },

    showTodo() {
      this.showCurrentTodo = true;
    }
  }
};
</script>

<style>
.container {
  display: flex;
  flex-direction: column;
  background-color: #15191b;
  color: aliceblue;
  padding: 5rem;
  gap: 2;
  height: 100vh;
}

.display {
  display: flex;
  flex-direction: column;
}

.heading {
  color: #eae287;
  font-weight: 600;
}
</style>
