<template>
  <section tabindex="2">
    <h2>Instructions</h2>
    <p>
      Use the
      <strong>Previous</strong> and
      <strong>Next</strong> buttons or
      <strong>Left</strong> and
      <strong>Right</strong> arrow keys to navigate through cards.
      <br>Press
      <strong>F</strong> or
      <strong>click/tap</strong> card to flip and display the answer.
    </p>
  </section>
</template>

<script>
</script>

<style scoped>
p {
  max-width: 33rem;
  text-align: left;
  padding: 20px;
  line-height: 1.5rem;
}

@media (max-width: 400px) {
  p {
    padding: 10px;
    font-size: 0.9rem;
  }
  h2 {
    font-size: 1.1rem;
  }
}
</style>