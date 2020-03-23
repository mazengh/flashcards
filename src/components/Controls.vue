<template>
  <nav class="controls">
    <button @click="onPreviousClicked" :disabled="previousDisabled">
      Previous
    </button>
    <button @click="onNextClicked" :disabled="nextDisabled">
      Next
    </button>
  </nav>
</template>

<script>
export default {
  name: "controls",
  props: {
    previousDisabled: Boolean,
    nextDisabled: Boolean
  },
  methods: {
    onPreviousClicked() {
      this.$emit("previousClicked");
    },
    onNextClicked() {
      this.$emit("nextClicked");
    }
  }
};
</script>

<style lang="scss" scoped>
@import "../scss/_variables.scss";

.controls {
  display: flex;
  justify-content: center;
  align-items: center;

  button {
    min-width: 5rem;
    border: 0;
    border-radius: 0.25rem;
    background-color: $blue-1;
    color: $white;
    font-size: 1rem;
    line-height: 1.2;
    white-space: nowrap;
    text-decoration: none;
    padding: 0.25rem 0.5rem;
    margin: 0.25rem 0.5rem;
    cursor: pointer;
    border: 2px solid transparent;

    &:focus,
    &:hover {
      border: 2px solid $blue-2;
      cursor: pointer;
    }

    &:disabled {
      background-color: $gray-1;
      color: $gray-2;
      text-decoration: line-through;
      cursor: not-allowed;
      &:hover {
        border: 2px solid transparent;
      }
    }
  }
}
</style>
