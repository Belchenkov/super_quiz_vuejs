<template>
  <div class="alert alert-success text-center">
    <h1>That's Correct!</h1>
    <hr>
    <button class="btn btn-info" @click="onNextQuestion">Next Question</button>
  </div>
</template>
<style scoped>
  .alert-success {
    width: 600px;
    height: 150px;
  }
</style>
<script>

  export default{
    methods: {
      onNextQuestion() {
        this.$emit('confirmed');
      }
    }
  }
</script>
