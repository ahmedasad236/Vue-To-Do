<template>
  <div class="container">
    <h1 class="heading">Todos</h1>
    <div class="display">
      <ul class="todos">
        <li
          class="todo"
          v-for="todo in todos"
          :key="todo"
        >
          <input
            type="checkbox"
            class="checkbox"
          />
          <sapn class="todo-text">{{ todo }}</sapn>
          <button
            @click="removeFromTodos(todo)"
            class="remove-btn"
          >
            &times;
          </button>
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
      <button
        class="show-btn"
        @click="showTodo()"
      >
        +
      </button>
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

.todos {
  list-style: none;
}

.todo {
  position: relative;
  background: #0e0f0f;
  padding: 2rem;
  border-radius: 10px;
}

.heading {
  color: #eae287;
  font-weight: 600;
}

.show-btn {
  border-radius: 5px;
  font-size: 1.2rem;
  text-align: center;
  width: 5%;
  background: #15191b;
  color: inherit;
  border: none;
  transition: all 0.2s;
  height: 40px;
}

.remove-btn {
  position: absolute;
  right: 2rem;
  border-radius: 50%;
  width: 30px;
  height: 30px;
  background: #2c2e2f;
  color: aliceblue;
  border: none;
  transition: all 0.2s;
}

.checkbox {
  width: 1rem;
  height: 1rem;
  margin-right: 2rem;
}

.todo-text {
  font-family: 'Courier New', Courier, monospace;
  font-weight: 500;
  font-size: 1.4rem;
}

.remove-btn:hover {
  background: rgb(222, 24, 24);
}

.show-btn:hover {
  border: 1px solid rgb(5, 93, 130);
}
</style>
