<template>
  <div>
    <div class="root">
    <h2>Атрибуты формы</h2>
    <p>
      <input type="text" placeholder="Фамилия" v-model="surename" />
    </p>
    <p>
      <input type="text" placeholder="Имя" v-model="idname"/>
    </p>
    <p>
      <input type="text" placeholder="Отчество" v-model="lastname"/>
    </p>
    <p>
      <input type="text" placeholder="Дата рождения" v-model="dob"/>
    </p>
    <p>
      <input type="text" placeholder="Номер телефона" v-model="telNumber"/>
    </p>
    <p>
      <input type="text" placeholder="Пол" v-model="sex"/>
    </p>
    
      <h3>Группа клиентов</h3>
      <select name="clients" id="client" multiple>
        
        <option value="VIP">VIP</option>
        <option value="Проблемные">Проблемные</option>
        <option value="ОМС">ОМС</option>
      </select>
    
    
      <br>
      <br>
      <label for="doctors">Лечащий врач:</label>
      <select name="doctors" id="doctors">
        
        <option></option>
        <option>Иванов</option>
        <option>Захаров</option>
        <option>Чернышева</option>
      </select>
    
     <p>
      <input type="checkbox" id="checkbox" v-model="checked">
      <label for="checkbox"> Не отправлять СМС </label>
    </p>

<h2>Адрес</h2>
    <p>
      <input type="text" placeholder="Индекс" v-model="index" />
    </p>
    <p>
      <input type="text" placeholder="Страна" v-model="country" />
    </p>
    <p>
      <input type="text" placeholder="Область" v-model="location" />
    </p>
    <p>
      <input type="text" placeholder="Город" v-model="city" />
    </p>
    <p>
      <input type="text" placeholder="Улица" v-model="street" />
    </p>
    <p>
      <input type="text" placeholder="Дом" v-model="hause" />
    </p>

    <h1>Паспорт</h1>
      <label for="passport">Тип документа:</label>
    
      <select> name="passport id="passport">
        
        <option></option>
        <option>Паспорт</option>
        <option>Свидетельство о рождении</option>
        <option>Вод. удостоверение</option>
      </select>
    
    <p>
      <input type="text" placeholder="Серия" v-model="series" />
    </p>
    <p>
      <input type="text" placeholder="azat" v-model="idNumber"
      />
    </p>
    <p>
      <input type="text" placeholder="Кем выдан" v-model="giver" />
    </p>
    <p>
      <input type="text" placeholder="Дата выдачи" v-model="dateOfGiven" />
    </p>
    <button @click="submitForm">Submit</button>
  </div>
  </div>

  
</template>

<script>
import useValidate from '@vuelidate/core'
import { required } from '@vuelidate/validators'
export default {
  data() {
    return {
        v$: useValidate(),
        surename: '',
        idname: '',
        dob: '',
        telNumber: '',
        city: '',
        series: '',
        dateOfGiven: '',
    }
  },
  validations() {
    const startWith7 = val => /^\+7[0-9-]+$/.test(val);

    return {
          surename: {required},
          idname: {required},
          dob: {required},
          telNumber: {required, startWith7},
          city: {required},
          series: {required},
          dateOfGiven: {required},
  
    }
  },

  methods: {
    submitForm() {
      this.v$.$validate()
      if (!this.v$.$error) {
        alert('Вы все заполнили верно')
      } else {
        console.log(this.v$.$errors)
        alert('Заполните пожалуйста необходимые поля')
      }
    },
  },
}
</script>


<style>


.root {
  width: 400px;
  margin: 0 auto;
  background-color: #fff;
  padding: 30px;
  margin-top: 100px;
  border-radius: 20px;
}



input {
  border: none;
  outline: none;
  border-bottom: 1px solid #ddd;
  font-size: 1em;
  padding: 5px 0;
  margin: 10px 0 5px 0;
  width: 100%;
}

button {
  background-color: #3498db;
  padding: 10px 20px;
  margin-top: 10px;
  border: none;
  color: white;
}
</style>