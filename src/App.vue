<template>
  <div id="app">
    <Spinner v-if="!deck" />
    <FlashCards v-else :deck="deck" />
  </div>
</template>

<script>
import axios from "axios";
import Spinner from "@/components/Spinner";
import FlashCards from "@/pages/FlashCards";
import americanFlag from "@/data/americanFlag.json";

export default {
  name: "app",
  components: { Spinner, FlashCards },
  data() {
    return {
      deck: null
    };
  },
  created() {
    // get the deck for questions about the American Flag
    const url = `https://flashcards-99bce.firebaseio.com/decks.json?orderBy="name"&equalTo="americanFlag"`;
    axios
      .get(url)
      .then(res => {
        this.deck = res.data[Object.keys(res.data)[0]];
      })
      .catch(err => {
        alert(err);
      })
      .finally(() => {
        if (!this.deck) {
          this.loadDefaultLocalDeck();
        }
      });
  },
  methods: {
    loadDefaultLocalDeck() {
      this.deck = americanFlag;
    }
  }
};
</script>

<style lang="scss">
@import "./scss/_variables.scss";

#app {
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
}
@import url("https://fonts.googleapis.com/css?family=Montserrat:400,500,600,700");

* {
  margin: 0;
  padding: 0;
  box-sizing: border-box;
}

html,
body {
  background-color: #fafafa;
  color: $gray-1;
  font-family: $fonts;
  box-sizing: border-box;
}
</style>
