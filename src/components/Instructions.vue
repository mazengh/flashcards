<template functional>
  <section class="instructions">
    <h2>Instructions</h2>
    <p>
      Use the
      <strong>Previous</strong> and <strong>Next</strong> buttons or
      <strong>Left</strong> and <strong>Right</strong> arrow keys to navigate
      through cards. <br />Press <strong>F</strong> or
      <strong>click/tap</strong> card to flip and display the answer.
    </p>
  </section>
</template>

<script></script>

<style lang="scss" scoped>
.instructions {
  display: flex;
  flex-direction: column;
  justify-content: center;
  align-items: center;
  p {
    max-width: 33rem;
    text-align: left;
    padding: 1.25rem;
    line-height: 1.5rem;
  }
}

@media (max-width: 400px) {
  .instructions {
    p {
      padding: 10px;
      font-size: 0.9rem;
    }
    h2 {
      font-size: 1.1rem;
    }
  }
}
</style>
