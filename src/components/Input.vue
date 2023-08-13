<template>
  <input />
</template>

<script>
export default {
  name: 'InputVue',
  props: {
    type: {
      type: String,
      default: 'text'
    },

    value: String,
    onClick: Function
  }
};
</script>

<style scoped></style>
