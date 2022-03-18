<template>
    <div class="col-md-2 col-lg-1">
      <label><strong>{{ label }}</strong></label>
      <input
        :ref="refName"
        type="text"
        placeholder="0"
        v-model="inputVal"
        @focus="$event.target.select()"
        class="form-control centered-input"
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
        return this.value || 0
      },
      set(val) {
        this.$emit('input', {val: parseInt(val) || 0, index: this.index})
      }
    },
    refName() {
      return (this.index == 0) ? 'firstInput' : 'other'
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

<style>
.centered-input {
  text-align: center;
}
</style>
