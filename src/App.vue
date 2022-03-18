<template>
  <div class="container">
    <wordle-averager />
  </div>
</template>

<script>
import WordleAverager from './components/WordleAverager.vue'

export default {
  name: 'App',
  components: { WordleAverager },
}
</script>
