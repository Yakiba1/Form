<template>
  <div class="form-control">
    <label>{{label}}</label>
    <input
        type="number"
        :max="max"
        v-model.number="localValue"
        @input="changeAge"
        >
  </div>
</template>

<script>
export default {
  emits: ['update:modelValue'],
  props: {
    modelValue: {
      type: Number,
      default: 0
    },
    label: String,
    max: Number
  },
  data() {
    return {
      localValue: this.modelValue
    }
  },
  methods: {
    changeAge() {
      this.$emit('update:modelValue', this.localValue); // Эмитируем обновленное значение
    }
  },
  watch: {
    modelValue(newWal) {
      this.localValue = newWal
    }
  }
}
</script>

<style lang="scss" scoped>

</style>
