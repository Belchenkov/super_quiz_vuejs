<template>
  <div class="container" id="app">
    <div class="row">
        <h1 class="text-center">The Super Quiz</h1>
        <hr>
    </div>
    <hr>
    <div class="row">
      <div>
        <component
          :is="mode"
          @answered="answered($event)"
          @confirmed="mode = 'app-question'"
        ></component>
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
  #app {
    display: flex;
    flex-direction: column;
    justify-content: center;
    align-items: center;
    width: 100vw;
    height: 100vh;
    padding-bottom: 250px;
  }
</style>
