<template>
  <div class="container">
    <h1 class="heading">Todos</h1>
    <div class="display">
      <ul class="todos">
        <li
          class="todo"
          v-bind:class="getTodo(todo).completed && 'completed-task'"
          v-for="todo in filteredTodos"
          :key="todo.todo"
        >
          <input
            type="checkbox"
            class="checkbox"
            v-bind:id="todo.todo"
            v-bind:value="getTodo(todo).completed"
            @click="toggleCompleted(todo)"
          />
          <label
            v-bind:for="todo.todo"
            class="todo-text"
            >{{ todo.todo }}</label
          >
          <button
            @click="removeFromTodos(todo)"
            class="remove-btn"
          >
            &times;
          </button>
        </li>
      </ul>
      <div
        style="
          margin-bottom: 1rem;
          display: flex;
          gap: 1rem;
          align-items: center;
        "
        v-if="showCurrentTodo"
      >
        <input
          v-model="currentTodo"
          id="enter-todo"
          placeholder="Enter todo..."
        />
        <button
          class="submit-todo"
          @click="addToTodo(currentTodo)"
        >
          &#x2713;
        </button>
      </div>
      <div class="events-box">
        <button
          class="primary-btn show-btn"
          @click="showTodo()"
        >
          +
        </button>

        <button
          v-if="todos.length && (showCompleted || showUnCompleted)"
          class="primary-btn filter-btn"
          @click="(showCompleted = false), (showUnCompleted = false)"
        >
          Show all Todos
        </button>
        <button
          v-if="todos.length && !showCompleted"
          class="primary-btn filter-btn"
          @click="(showCompleted = true), (showUnCompleted = false)"
        >
          Filter completed tasks
        </button>

        <button
          class="primary-btn filter-btn"
          @click="(showUnCompleted = true), (showCompleted = flse)"
          v-if="todos.length && !showUnCompleted"
        >
          Filter uncompleted tasks
        </button>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: 'App',
  data() {
    return {
      todos: [],
      currentTodo: '',
      showCurrentTodo: false,
      showCompleted: false,
      showUnCompleted: false
    };
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

    addToTodo(todo) {
      if (!this.currentTodo) return;

      if (!this.todos.find((item) => item.todo === todo))
        this.todos.push({ todo, completed: false });
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
  display: flex;
  flex-direction: column;
  gap: 1rem;
  padding: 0;
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

#enter-todo {
  background: #15191b;
  color: aliceblue;
  padding: 2rem;
  flex-basis: 95%;
  border: none;
  border-radius: 10px;
  font-size: 1.1rem;
}

.submit-todo {
  width: 2rem;
  height: 2rem;
  border: none;
  background: #15191b;
  color: aliceblue;
}

.primary-btn {
  border-radius: 5px;
  font-size: 1.2rem;
  text-align: center;
  background: #15191b;
  color: inherit;
  border: none;
  transition: all 0.2s;
}

.events-box {
  display: flex;
  align-items: center;
  justify-content: space-between;
}

.show-btn {
  width: 5%;
  height: 40px;
}

.filter-btn {
  padding: 1rem;
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
  font-weight: 700;
  font-size: 1.4rem;
}

.remove-btn:hover {
  background: rgb(222, 24, 24);
}

.completed-task {
  background: rgb(25, 112, 25);
}

.primary-btn:hover {
  border: 1px solid rgb(5, 93, 130);
}
</style>
