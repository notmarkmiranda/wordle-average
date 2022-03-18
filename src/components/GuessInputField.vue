<template>
  <div class="col-1">
    <label><strong>{{ label }}</strong></label>
    <input
      :ref="refName"
      type="number"
      placeholder="0"
      v-model="inputVal"
      @focus="$event.target.select()"
      class="form-control form-control-lg"
    >
  </div>
</template>

<script>
export default {
  name: 'GuessInputField',
  props: {
    value: {
      type: Number,
      default: 0
    },
    label: {
      type: String,
      required: true,
    },
    index: {
      type: Number,
      required: true,
    }
  },
  computed: {
    inputVal: {
      get() {
        return this.value
      },
      set(val) {
        console.log('HELP', val);
        this.$emit('input', {val: val, index: this.index})
      }
    },
    refName() {
      if (this.index == 0) {
        return 'firstInput'
      } else {
        return 'other'
      }
    }
  },
  methods: {
    focusInput() {
      if (this.$refs.firstInput) {
        this.$refs.firstInput.focus()
      }
    }
  },
  mounted() {
    this.focusInput()
  }
}
</script>
