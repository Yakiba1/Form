<template>
  <div class="form-control">
    <label :for="id">{{label}}</label>
    <select :id="id"
            :value="modelValue"
            @input="changeCity">
      <option value="spb">Санкт-Петербург</option>
      <option value="msk">Москва</option>
      <option value="kzn">Казань</option>
      <option value="nsk">Новосибирск</option>
    </select>
  </div>
</template>

<script>

export default {
  emits:['update:modelValue'],
  props: {
    label: String,
    modelValue: String,
  },
  methods: {
    changeCity(event) {
      this.$emit('update:modelValue', event.target.value)
    }
  },
  data() {
    return {
      id: 'select-' + Math.random()
    }
  }
}
</script>

<style lang="scss" scoped>

</style>
