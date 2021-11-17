<!-- Template tag can contain only one child element  -->
<template>
  <div id="app">

    <h1>Would you rather?</h1>

    <would-you-rather
        v-for="question in questions"
        v-bind:question="question.question"
        v-bind:answer1="question.answer1"
        v-bind:answer2="question.answer2"
        v-on:answer-changed="answerChanged"
    ></would-you-rather>
    <!-- v-bind is used in this case to bind a child prop value to a parent data value from the parent component
       v-bind:{child prop value}="{parent data value}" -->
    <!-- valid HTML tags do not contain dashes - dash notation prevents conflicts -->
    <!-- events: dashes (avoid conflicts)  methods: camel case -->

    <h2>You Would Rather:</h2>
    <ul>
      <li v-for="question in questions" v-show="question.userSelection">{{question.userSelection}}</li>
    </ul>

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

        questions: [
          {
            id: 0,
            question: '...start a colony on another planet or be the leader of a small country on Earth?',
            answer1: 'Start a colony on another planet',
            answer2: 'Be the leader of a small country on earth',
            userSelection: ''
          },
          {
            id: 1,
            question: '...be able to change the color of anything with just a thought or know every ' +
                'language that has ever been spoken on Earth?',
            answer1: 'Change the color of anything with just a thought',
            answer2: 'Know every language ever spoken on Earth',
            userSelection: ''
          },
          {
            id: 2,
            question: '...be able to remember everything in every book you read or remember every conversation you have?',
            answer1: 'Remember everything in every book you read',
            answer2: 'Remember every conversation you have',
            userSelection: ''
          },
        ],

      }
  },

  methods: {
    answerChanged(choice) {
      this.questions.forEach((q) => {
        if (q.answer1 === choice || q.answer2 === choice) {
          q.userSelection = choice
        }
      })

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

li {
  alignment: center;
  list-style-type: none;
  padding: 0;
  margin: 0;
}

body {
  background: cadetblue;
}
</style>
