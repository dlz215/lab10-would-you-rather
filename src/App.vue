<!-- Template tag can contain only one child element  -->
<template>
  <div id="app">

    <h1>Would you rather...</h1>

    <would-you-rather
        v-bind:question="wyrQuestion"
        v-bind:answer1="wyrAnswer1"
        v-bind:answer2="wyrAnswer2"
        v-on:answer-changed="answerChanged"
    ></would-you-rather>
    <!-- v-bind is used in this case to bind a child prop value to a parent data value from the parent component
       v-bind:{child prop value}="{parent data value}" -->
    <!-- valid HTML tags do not contain dashes - dash notation prevents conflicts -->
    <!-- events: dashes (avoid conflicts)  methods: camel case -->

    <p>{{ userSelectionMessage }}</p>

  </div>
</template>

<script>
import WouldYouRather from './components/WouldYouRather.vue'

export default {

  name: 'App',

  components: {
    WouldYouRather
  },

  data() {
      return {
        wyrQuestion: 'Would you rather start a colony on another planet or be the leader of a small country on Earth?',
        wyrAnswer1: 'Colony on another planet',
        wyrAnswer2: 'Small country on earth',
        userSelectionMessage: ''
      }
  },

  methods: {
    answerChanged(choice) {
      this.userSelectionMessage = `Thanks! You chose ${choice}`
    }
  }

}

</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
  margin-left: 30px;
  margin-right: 30px;
  padding: 10px;
  background: lightgreen;

}

body {
  background: cadetblue;
}
</style>
