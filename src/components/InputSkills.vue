<template>
  <div class="form-checkbox">
    <span class="label">{{label}}</span>
    <div class="checkbox"
         v-for="(skill, index) in availableSkills"
         :key="index">
      <label><input type="checkbox"
                    :value="skill"
                    name="checkbox"
                    :checked="modelValue.includes(skill)"
                    @change="changeSkills"/>
        {{skill}}</label>
    </div>
  </div>
</template>

<script>
    export default {
      emits:["update:modelValue"],
      props:{
        label:String,
        modelValue: {
          type: Array,
          default: () => []
        }
      },
      data() {
        return {
          availableSkills: ['Vuex', 'Vue CLI', 'Vue Router']
        }
      },
      methods: {
        changeSkills(event) {
          const value = event.target.value;
          const checked = event.target.checked;

          let updatedSkills = [...this.modelValue];

           if (checked) {
             // Добавляем выбранный навык
            if (!updatedSkills.includes(value)) {
            updatedSkills.push(value);
           }
           } else {
             // Удаляем невыбранный навык
            updatedSkills = updatedSkills.filter(skill => skill !== value);
           }

          this.$emit('update:modelValue', updatedSkills);
        }
      }
    }
</script>

<style lang="scss" scoped>

</style>
