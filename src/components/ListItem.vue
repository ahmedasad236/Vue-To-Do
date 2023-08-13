<template>
  <li
    class="todo"
    v-bind:class="getTodo(todo).completed && 'completed-task'"
  >
    <input
      type="checkbox"
      class="checkbox"
      v-bind:id="todo.todo"
      v-bind:checked="getTodo(todo).completed"
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
</template>

<script>
export default {
  name: 'ListItemVue',
  props: {
    todo: Object,
    getTodo: Function,
    removeFromTodos: Function,
    toggleCompleted: Function
  }
};
</script>

<style scoped>
.todo {
  position: relative;
  background: #0e0f0f;
  padding: 2rem;
  border-radius: 10px;
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

.completed-task {
  background: rgb(25, 112, 25);
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
</style>
