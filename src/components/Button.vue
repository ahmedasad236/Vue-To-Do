<template>
  <button
    @click="callOnClick"
    v-bind:class="classes.join(' ')"
  >
    <slot></slot>
  </button>
</template>

<script>
export default {
  name: 'ButtonVue',
  props: {
    onClick: Function,
    text: String,
    classes: Array,
    todo: { type: Object, default: null }
  },

  methods: {
    callOnClick() {
      if (this.todo) this.onClick(this.todo);
      else this.onClick();
    }
  }
};
</script>

<style scoped></style>
