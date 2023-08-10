<template>
  <div :class="container">
    <h1 :class="heading">To Do list</h1>
    <form></form>
  </div>
</template>

<script>
export default {
  name: 'App'
};
</script>

<style>
.container {
  display: flex;
  flex-direction: column;
  justify-content: center;
  align-items: center;
  background-color: #ccc;
  padding: 2rem;
  gap: 2;
}

.heading {
  color: rgb(36, 53, 87);
  font-weight: 600;
}
</style>
