<template>
  <div class="container">
    <form class="card" @submit.prevent="submitForm">
      <h1>Анкета на Vue разработчика!</h1>
      <InputName
      placeholder="Введите имя"
      :error="error.name"
      label="Как тебя зовут"
      v-model="name">
      </InputName>

      <InputAge
      label="Выбери возраст"
      :max="70"
      v-model="age"
      >
      </InputAge>

      <ImportCity
      label="Твой город"
      v-model="city">
      </ImportCity>

      <InputMove
      label="Готов к переезду в Токио ?"
      v-model="relocate">
      </InputMove>


      <InputSkills
        v-model="skill"
        label="Что знаешь о vue?">
      </InputSkills>

      <button type="submit" class="btn primary">Отправить</button>
    </form>
  </div>
</template>

<script>
import InputAge from "@/components/InputAge.vue";
import InputName from "@/components/InputName.vue";
import ImportCity from "@/components/ImportCity.vue";
import InputMove from "@/components/InputMove.vue";
import InputSkills from "@/components/InputSkills.vue";

export default {
  components: {InputSkills, InputMove, ImportCity, InputName, InputAge},
  data () {
    return {
      name: '',
      age: 23,
      city: 'nsk',
      relocate: 'yes',
      skill: [],
      error: {
        name: null
      }
    }
  },
  methods:{
    formIsValid () {
      let isValid = true;
      if (this.name.length === 0) {
        this.error.name = 'Введите имя'
        isValid = false;
      } else {
        this.error.name = null
      }
      return isValid
    },
    submitForm(){
      if (this.formIsValid()) {
        console.group('Form data')
        console.log('name: ', this.name);
        console.log('age: ', this.age); //parseInt() преобразует строку в Number
        console.log('city: ', this.city);
        console.log('readyOrNot:', this.relocate);
        console.log('skill:', this.skill);
        console.groupEnd()

        this.name = ''; // Сбрасываем поле name
        this.skill = []; // Сбрасываем массив skill
        this.age = 23; // Вернуть к значению по умолчанию, если необходимо
        this.city = 'nsk'; // Вернуть к значению по умолчанию, если необходимо
        this.relocate = 'yes'; // Вернуть к значению по умолчанию
      }
    }
  }
}
</script>

