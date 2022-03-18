<template>
  <div class="mt-4 text-center">
    <h1>Wordle Averager!</h1>
    <hr />
    <h3>Guess Distribution</h3>
    <div class="row justify-content-center mb-4">
      <guess-input-field
        v-for="(guess, index) in guessDistribution"
        :key="index"
        :index="index"
        :label="(index + 1).toString()"
        :value="guessDistribution[index]"
        @input="setGuess"
      />
    </div>
    <div class="col">
      <h3>Total Number of successful plays: {{ numberOfPlays }}</h3>
      <h3>Total Number of guesses: {{ sumOfGuesses }}</h3>
      <h3>Average number of guesses: {{average}}</h3>
    </div>
  </div>
</template>

<script>
import GuessInputField from './GuessInputField.vue'

export default {
  name: 'WordleAverager',
  components: { GuessInputField },
  data() {
    return {
      guessDistribution: [2, 4, 16, 18, 8, 3]
    }
  },
  computed: {
    numberOfPlays() {
      return this.guessDistribution.reduce((acc, val) => acc + val, 0)
    },
    sumOfGuesses() {
      return this.guessDistribution.reduce((acc, val, index) => acc + ((index + 1) * val), 0)
    },
    average() {
      return (this.sumOfGuesses / this.numberOfPlays).toFixed(3)
    },
    computeRef(index) {
      if (index==0) {
        return 'first'
      } else {
        return 'other'
      }
    }
  },
  methods: {
    setGuess(obj) {
      this.guessDistribution[obj.index] = obj.val
    },
  },
}
</script>
