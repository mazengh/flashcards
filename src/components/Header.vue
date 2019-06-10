<template>
  <header>
    <div>
      <font-awesome-icon :icon="['fa', 'bolt']" size="2x" border fixed-width class="logo"/>
      <h1 tabindex="1">{{title}}</h1>
    </div>
  </header>
</template>

<script>
export default {
  name: "Header",
  props: {
    title: String
  }
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
  padding: 20px 0;
  margin-bottom: 30px;
  text-transform: capitalize;
  border-bottom: 2px solid $blue-2;
  display: flex;
  justify-content: space-between;
  height: 15vh;
}

header div {
  width: 100%;
  margin: auto;
  display: flex;
  justify-content: center;
  align-items: center;

  h1 {
    display: inline-block;
    margin-left: 1rem;
  }
}

@media (max-width: 400px) {
  header {
    padding: 8px 0;
    margin: 15px 0;
    div {
      h1 {
        font-size: 1.2rem;
      }
    }
  }
}
</style>