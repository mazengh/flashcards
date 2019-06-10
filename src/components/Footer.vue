<template>
  <footer>
    <nav class="controls">
      <ul>
        <li>
          <button
            tabindex="5"
            @click="onPreviousClicked"
            :disabled="!this.currentCardIndex"
          >Previous</button>
        </li>
        <li>
          <button
            tabindex="6"
            @click="onNextClicked"
            :disabled="this.currentCardIndex === this.totalCards - 1"
          >Next</button>
        </li>
      </ul>
    </nav>
  </footer>
</template>

<script>
export default {
  name: "Footer",
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

footer {
  height: 15vh;
  display: flex;
  justify-content: center;
  align-items: center;

  nav.controls ul {
    display: flex;
    align-items: baseline;
    list-style-type: none;

    li button {
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
      // &:hover:not(:disabled) {
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