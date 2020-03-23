<template functional>
  <header>
    <!-- <div> -->
    <font-awesome-icon
      :icon="['fa', 'bolt']"
      size="2x"
      border
      fixed-width
      class="logo"
    />
    <h1>{{ props.title }}</h1>
    <!-- </div> -->
  </header>
</template>

<script>
export default {
  name: "Header"
};
</script>

<style lang="scss" scoped>
@import "../scss/_variables.scss";

.logo {
  display: inline-block;
  color: $flash;
  border-color: $gray-2;
}

header {
  color: $gray-1;
  padding: 3rem 0 1rem;
  margin-bottom: 30px;
  text-transform: capitalize;
  border-bottom: 2px solid $blue-2;
  display: flex;
  justify-content: center;
  align-items: center;
  justify-content: center;
  h1 {
    font-size: calc(1rem + 1.5vmin);
    text-align: left;
    margin-left: 1rem;
  }
}

@media (max-width: 400px) {
  header {
    padding: 0.5rem 0;
    margin: 1rem 0;
    div {
      h1 {
        font-size: 1.2rem;
      }
    }
  }
}
</style>
