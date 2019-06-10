<template>
  <Spinner v-if="!cards"/>
  <div v-else id="app" class="container">
    <Header :title="getTitle()"/>

    <div class="wrapper">
      <Instructions/>
      <Card
        :isQuestion="isQuestion"
        :question="getQuestion()"
        :answer="getAnswer()"
        @clicked="flipCard"
      />
    </div>

    <Footer
      :nextHandler="next"
      @previousClicked="previous"
      @nextClicked="next"
      :totalCards="totalCards"
      :currentCardIndex="currentCardIndex"
    />
  </div>
</template>

<script>
import axios from "axios";

import Header from "./components/Header.vue";
import Footer from "./components/Footer.vue";
import Instructions from "./components/Instructions.vue";
import Card from "./components/Card.vue";
import Spinner from "./components/Spinner";

export default {
  name: "app",
  data() {
    return {
      isQuestion: true,
      cards: null,
      currentCardIndex: 0,
      totalCards: 0
    };
  },
  mounted() {
    window.addEventListener("keydown", this.handleKeys);
  },
  methods: {
    setCards(cards) {
      this.cards = cards;
      this.totalCards = cards.questions.length;
    },
    getTitle() {
      return this.cards.title;
    },
    getQuestion() {
      return this.cards.questions[this.currentCardIndex];
    },
    getAnswer() {
      return this.cards.answers[this.currentCardIndex];
    },
    flipCard() {
      this.isQuestion = !this.isQuestion;
    },
    handleKeys(event) {
      //if the F key was pressed
      if (event.which === 70) {
        this.flipCard();
      }
      //if the left arrow key was pressed
      else if (event.which === 37) {
        this.previous();
      }
      //if the Right arrow key was pressed
      else if (event.which === 39) {
        this.next();
      }
    },
    next(btn) {
      if (this.currentCardIndex < this.totalCards - 1) {
        this.currentCardIndex++;
        this.isQuestion = true;

        // below code is required for firefox when clicked button gets disabled
        if (this.currentCardIndex === this.totalCards - 1 && btn) {
          btn.blur();
        }
      }
    },
    previous(btn) {
      if (this.currentCardIndex > 0) {
        this.currentCardIndex--;
        this.isQuestion = true;

        // below code is required for firefox when clicked button gets disabled
        if (this.currentCardIndex === 0 && btn) {
          btn.blur();
        }
      }
    }
  },
  components: {
    Header,
    Footer,
    Instructions,
    Card,
    Spinner
  },
  created() {
    // get the deck for questions about the American Flag
    const url = `https://flashcards-99bce.firebaseio.com/decks.json?orderBy="name"&equalTo="americanFlag"`;
    axios
      .get(url)
      .then(res => {
        this.setCards(res.data[Object.keys(res.data)[0]]);
      })
      .catch(err => {
        alert(err);
      });
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
  background-color: #eee;
  color: $gray-1;
  font-family: $fonts;
  font-weight: 400;
  height: 100vh;
  box-sizing: border-box;
}

.container {
  max-width: 850px;
  margin: 0 auto;
  padding: 0 40px;
  display: flex;
  flex-direction: column;
  background-color: $white;
  height: 100vh;

  .wrapper {
    display: flex;
    flex-direction: column;
    height: 70vh;
    margin-bottom: 30px;
    justify-content: center;
    align-items: center;
  }
}
</style>
