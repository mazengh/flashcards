<template>
  <nav class="controls">
    <ul>
      <li>
        <button @click="onPreviousClicked" :disabled="!this.currentCardIndex">
          Previous
        </button>
      </li>
      <li>
        <button
          @click="onNextClicked"
          :disabled="this.currentCardIndex === this.totalCards - 1"
        >
          Next
        </button>
      </li>
    </ul>
  </nav>
</template>

<script>
export default {
  name: "controls",
  props: {
    currentCardIndex: Number,
    totalCards: Number
  },
  methods: {
    onPreviousClicked(event) {
      this.$emit("previousClicked", event.target);
    },
    onNextClicked(event) {
      this.$emit("nextClicked", event.target);
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

  ul {
    display: flex;
    align-items: baseline;
    list-style-type: none;

    li button {
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
}
</style>
