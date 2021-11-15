<template>
  <div class="wyr">

    <h2>Please make your choice!</h2>

    <h3>{{ question }}</h3>

    <input type="radio" v-model="choice" v-bind:value="answer1" v-on:change="choiceMade">
    <label>{{ answer1 }}</label>

    <input type="radio" v-model="choice" v-bind:value="answer2" v-on:change="choiceMade">
    <label>{{ answer2 }}</label>
    <!-- v-bind is used in this case to bind an HTML attribute to a prop value within the child component -->
    <!-- radio buttons emit a change event when selected   v-on:change="{method name}"-->

  </div>
</template>

<script>

export default {

  name: 'WouldYouRather',

  /* Data sent from parent component to child is stored in props.
  Props: provided by parent component. Data: stored or generated internally. */
  props: {
    question: String,
    answer1: String,
    answer2: String
  },

  /* Need to have a data function (instead of a simple data object) so values can be different and distinct across
  different instances of a component. Component may have several instances if it is reused by the program. */
  data() {
    return {
      choice: ''
    }
  },

  methods: {
    choiceMade() {
      this.$emit('answer-changed', this.choice)
      /* Emits an event. Only parent component can detect and receive event. */
      /* this.choice can be passed as parameter to a corresponding method in parent object triggered by answer-changed event */
    }
  }

}

</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
h3 {
  margin: 40px 0 0;
}

.wyr {
  border: 2px black solid;
  padding: 10px;
  background: lightblue;
  margin: 30px;
}

</style>
