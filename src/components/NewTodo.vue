<template>
  <div
    style="margin-bottom: 1rem; display: flex; gap: 1rem; align-items: center"
    v-if="showCurrentTodo"
  >
    <input
      @change="onChangeCurrentTodo"
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
</template>

<script>
export default {
  name: 'newTodo',
  props: {
    showCurrentTodo: Boolean,
    addToTodo: Function,
    currentTodo: String,
    onChangeCurrentTodo: Function
  }
};
</script>

<style scoped>
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
</style>
