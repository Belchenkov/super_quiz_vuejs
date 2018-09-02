<template>
  <div class="container" id="app">
    <div class="row">
        <h1 class="header text-center">The Super Quiz</h1>
        <hr>
    </div>
    <hr>
    <div class="row">
      <div>
        <transition name="flip" mode="out-in">
          <component
            :is="mode"
            @answered="answered($event)"
            @confirmed="mode = 'app-question'"
          ></component>
        </transition>
      </div>
    </div>
  </div>
</template>

<script>
  import Question from './components/Question';
  import Answer from './components/Answer';

export default {
  data () {
    return {
      mode: 'app-question'
    }
  },
  methods: {
    answered (isCorrect) {
      if (isCorrect) {
        this.mode = 'app-answer';
      } else {
        this.mode = 'app-question';
        alert('Wrong, try again!');
      }
    }
  },
  components: {
    appQuestion: Question,
    appAnswer: Answer
  }
}
</script>

<style>
  body {
    background: url("./assets/img/wavy-dots.png");

  }
  .header {
    font-family: Algerian, sans-serif;
  }

  #app {
    display: flex;
    flex-direction: column;
    justify-content: center;
    align-items: center;
    width: 100vw;
    height: 100vh;
    margin-top: -100px;
  }

  .flip-enter {
    transform: rotateY(90deg);
  }

  .flip-enter-active {
    animation: flip-in .5s ease-out forwards;
  }

  .flip-leave {
    transform: rotateY(0deg);
  }

  .flip-leave-active {
    animation: flip-out .5s ease-out forwards;
  }

  @keyframes flip-out {
    from {
      transform: rotateY(0deg);
    }
    to {
      transform: rotateY(90deg);
    }
  }

  @keyframes flip-in {
    from {
      transform: rotateY(90deg);
    }
    to {
      transform: rotateY(0deg);
    }
  }

</style>
