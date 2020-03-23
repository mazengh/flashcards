<template>
  <div class="flash-cards">
    <Header :title="deckTitle" />
    <main>
      <Instructions />
      <Card
        class="flash-cards__card"
        :flipped="flipped"
        @flipped="flipped = !flipped"
      >
        <template #front>
          <h3>Question?</h3>
          <div>
            <p>{{ currentQuestion }}</p>
          </div>
        </template>
        <template #back>
          <h3>Answer!</h3>
          <div>
            <p>{{ currentAnswer }}</p>
          </div>
        </template>
      </Card>
      <controls
        @previousClicked="previous"
        @nextClicked="next"
        :countOfCards="countOfCards"
        :currentCardIndex="currentCardIndex"
      />
    </main>
  </div>
</template>

<script>
import Header from "@/components/Header.vue";
import Controls from "@/components/Controls.vue";
import Instructions from "@/components/Instructions.vue";
import Card from "@/components/Card.vue";

export default {
  name: "flash-cards",
  components: {
    Header,
    Controls,
    Instructions,
    Card
  },
  props: {
    deck: {
      type: Object,
      required: true
    }
  },
  data() {
    return {
      currentCardIndex: 0,
      flipped: false
    };
  },
  computed: {
    deckTitle() {
      return this.deck.title;
    },
    questions() {
      return this.deck.questions;
    },
    currentQuestion() {
      return this.deck.questions[this.currentCardIndex];
    },
    currentAnswer() {
      return this.deck.answers[this.currentCardIndex];
    },
    countOfCards() {
      return this.questions.length;
    }
  },
  mounted() {
    window.addEventListener("keydown", this.handleKeys);
  },
  methods: {
    handleKeys(event) {
      //if the F key was pressed
      if (event.which === 70) {
        this.flipped = !this.flipped;
        // this.flipCard();
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
    next() {
      if (this.currentCardIndex < this.countOfCards - 1) {
        this.flipped = false;
        this.currentCardIndex++;
      }
    },
    previous() {
      if (this.currentCardIndex > 0) {
        this.currentCardIndex--;
        this.flipped = false;
      }
    }
  }
};
</script>

<style lang="scss" scoped>
@import "../scss/_variables.scss";

.flash-cards {
  max-width: 53rem;
  margin: 0 auto;
  padding: 0 40px;
  display: flex;
  flex-direction: column;
  align-items: center;
  background-color: $white;
  height: 100vh;

  &__card {
    height: 20rem;
    width: 90%;
    max-width: 33rem;
    margin: 1rem auto;
  }
}
</style>
