<template>
  <div class="cardContainer" @click="onClickCard">
    <div ref="currentCard" class="card" v-bind:class="{ 'flip': !isQuestion }">
      <div class="front">
        <h3>Question?</h3>
        <div>
          <p>{{question}}</p>
        </div>
      </div>
      <div class="back">
        <h3>Answer!</h3>
        <div>
          <p>{{answer}}</p>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: "Card",
  props: {
    isQuestion: Boolean,
    question: String,
    answer: String
  },
  methods: {
    onClickCard() {
      this.$emit("clicked");
    }
  }
};
</script>

<style lang="scss" scoped>
@import "../scss/_variables.scss";

div.cardContainer {
  position: relative;
  height: 20rem;
  width: 90%;
  max-width: 33rem;
  box-sizing: border-box;
  margin-top: 10px;
  padding: 15px;
  display: flex;
  flex-direction: column;
  justify-content: center;
  align-items: center;
  font-size: 1.3rem;
  background: none;
  perspective: 2000px;
  cursor: pointer;

  div.card {
    position: absolute;
    top: 0;
    left: 0;
    width: 100%;
    height: 100%;
    transform-style: preserve-3d;
    transition: all 0.8s ease;

    div.front,
    div.back {
      position: absolute;
      top: 0;
      left: 0;
      width: 100%;
      height: 100%;
      box-shadow: 2px 2px 2px $blue-2;
      border: 1px solid $blue-1;
      border-radius: 8px;
      backface-visibility: hidden;
      overflow: hidden;
      display: flex;
      flex-direction: column;
      justify-content: center;
      align-items: center;

      div p {
        text-align: left;
        margin: 10px;
      }
    }

    div.front {
      background: $green-1;
    }

    div.back {
      background: $blue-2;
      transform: rotateY(180deg);
    }
  }

  .flip {
    transform: rotateY(180deg);
  }
}
</style>