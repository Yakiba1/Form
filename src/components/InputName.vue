<template>
  <div class="form-control" :class="{invalid: error}">
    <label :for="id">{{label}}</label>
    <input
        type="text"
        :id="id"
        :placeholder="placeholder"
        :value="modelValue"
        @input="change">
    <small class="errorName" v-if="error">{{error}}</small>
  </div>
</template>

<script>
export default {
  emits: ['update:modelValue'],
  props: {
    modelValue: String,
    placeholder: String,
    error: String,
    label: String
  },
  methods: {
    change (event) {
      this.$emit('update:modelValue', event.target.value)
    }
  },
  data() {
    return {
    id:'input-' + Math.random()
    }
  }
}
</script>

<style scoped>
.form-control small {
  color: red;
}
.form-control.invalid input {
  border-color: red;
}
</style>
