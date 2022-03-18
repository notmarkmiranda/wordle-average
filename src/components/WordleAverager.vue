<template>
  <div class="mt-4 text-center">
    <h1>Wordle Averager!</h1>
    <h3>Guess Distribution</h3>
    <div class="row justify-content-center">
      <guess-input-field label="1" />
      <guess-input-field label="2" />
      <guess-input-field label="3" />
      <guess-input-field label="4" />
      <guess-input-field label="5" />
      <guess-input-field label="6" />
    </div>
  </div>
</template>

<script>
import GuessInputField from './GuessInputField.vue'

export default {
  name: 'WordleAverager',
  components: { GuessInputField },
}
</script>
