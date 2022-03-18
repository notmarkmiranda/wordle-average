<template>
  <div class="col-1">
    <label><strong>{{ label }}</strong></label>
    <input type="text" class="form-control form-control-lg">
  </div>
</template>

<script>
export default {
  name: 'GuessInputField',
  props: {
    label: {
      type: String,
      required: true,
    },
  }
}
</script>
