<template>
  <div class="mt-4 text-center">
    <h1>Wordle Averager!</h1>
    <hr />
    <h3>Guess Distribution</h3>
    <div class="row justify-content-center mb-4">
      <template v-for="(guess, index) in guessDistribution" :key="index">
        <guess-input-field
          :index="index"
          :label="(index + 1).toString()"
          :value="guessDistribution[index]"
          @input="setGuess"
        />
      </template>
    </div>
    <div class="col">
      <h3>Total number of successful plays: {{ numberOfPlays }}</h3>
      <h3>Total number of guesses: {{ sumOfGuesses }}</h3>
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
      guessDistribution: [0, 0, 0, 0, 0, 0]
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
      if (this.numberOfPlays == 0) { return 0 }
      return (this.sumOfGuesses / this.numberOfPlays).toFixed(3)
    },
  },
  methods: {
    setGuess(obj) {
      this.guessDistribution[obj.index] = obj.val
    },
  },
}
</script>
