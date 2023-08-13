<template>
  <div class="actions-box">
    <button
      class="primary-btn show-btn"
      @click="showTodo()"
    >
      +
    </button>

    <button
      v-if="todosLength && (showCompleted || showUnCompleted)"
      class="primary-btn filter-btn"
      @click="showAllTodosHandler"
    >
      Show all Todos
    </button>
    <button
      v-if="todosLength && !showCompleted"
      class="primary-btn filter-btn"
      @click="showCompletedTodosHandler"
    >
      Filter completed tasks
    </button>

    <button
      class="primary-btn filter-btn"
      @click="showUnCompletedTodosHandler"
      v-if="todosLength && !showUnCompleted"
    >
      Filter uncompleted tasks
    </button>
  </div>
</template>

<script>
export default {
  name: 'ActionBox',
  props: {
    showUnCompleted: Boolean,
    showCompleted: Boolean,
    todosLength: Number,
    showTodo: Function,
    showAllTodosHandler: Function,
    showCompletedTodosHandler: Function,
    showUnCompletedTodosHandler: Function
  }
};
</script>

<style scoped>
.actions-box {
  display: flex;
  align-items: center;
  justify-content: space-between;
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
.primary-btn:hover {
  border: 1px solid rgb(5, 93, 130);
}

.show-btn {
  width: 5%;
  height: 40px;
}

.filter-btn {
  padding: 1rem;
}

.remove-btn:hover {
  background: rgb(222, 24, 24);
}
</style>
