<template>
  <div class="form-checkbox">
    <span class="label">{{label}}</span>
    <div class="checkbox">
      <label><input
          type="radio"
          name="trip"
          value="yes"
          :checked="modelValue === 'yes'"
          @input="changeMove"
      /> Да</label>
    </div>

    <div class="checkbox">
      <label><input
          type="radio"
          name="trip"
          value="no"
          :checked="modelValue === 'no'"
          @input="changeMove"
      /> Нет</label>
    </div>
  </div>
</template>

<script>
export default {
  emits:["update:modelValue"],
  props: {
    label:String,
    modelValue: {
      type: String,
      default: 'yes'
    }
  },
  methods: {
    changeMove(event) {
      this.$emit('update:modelValue', event.target.value)
    }
  },
}
</script>

<style lang="scss" scoped>

</style>
