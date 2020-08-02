<template>
  <div class="SubmitForm">
    <div class="Form">
      <form class="formValidation" @submit.prevent="submitForm">
        <label for="surname">
          Фамилия
          <input type="text" v-model.trim="surname" class="notreq" /> </label
        ><br />
        <div class="error" v-if="!$v.surname.required && !$v.surname.$dirty">
          это поле обязательно
        </div>
        <div class="error" v-if="!$v.surname.minLength">
          минимальное количество символов
          {{ $v.surname.$params.minLength.min }}.Вы ввели
          {{ surname.length }}
        </div>
        <label for="name"
          >Имя <input type="text" v-model.trim="name" class="notreq"/></label
        ><br />
        <div class="error" v-if="!$v.name.required && !$v.name.$dirty">
          это поле обязательно
        </div>
        <div class="error" v-if="!$v.name.minLength">
          минимальное количество символов {{ $v.name.$params.minLength.min }}.Вы
          ввели
          {{ name.length }}
        </div>
        <label for="patronymic"
          >Отчество
          <input type="text" v-model.trim="patronymic" class="notreq"/></label
        ><br />

        <label for="birthday"
          >дата рождения
          <input type="date" v-model="birthday" class="notreq"/></label
        ><br />
        <div class="error" v-if="!$v.birthday.required && !$v.birthday.$dirty">
          это поле обязательно
        </div>
        <label for="numberPhone"
          >номер телефона
          <input type="text" v-model.trim="numberPhone" class="notreq"/></label
        ><br />
        <div
          class="error"
          v-if="!$v.numberPhone.required && !$v.numberPhone.$dirty"
        >
          это поле обязательно
        </div>
        <div class="error" v-if="!$v.numberPhone.minLength">
          минимальное количество символов
          {{ $v.numberPhone.$params.minLength.min }}.Вы ввели
          {{ numberPhone.length }}
        </div>
        <label for="sex"
          >пол
          <select v-model="sex" class="notreq">
            <option>Мужчина</option>
            <option>Женщина</option>
          </select> </label
        ><br />

        <label for="groupClients">
          Группа клиентов
          <select v-model="groupClients" class="notreq">
            <option>VIP</option>
            <option>Проблемные</option>
            <option>ОМС</option>
          </select> </label
        ><br />
        <div
          class="error"
          v-if="!$v.groupClients.required && !$v.groupClients.$dirty"
        >
          это поле обязательно
        </div>
        <label for="doctor">
          лечащий врач
          <select v-model="doctor" class="notreq">
            <option>Иванов</option>
            <option>Захаров</option>
            <option>Чернышева</option>
          </select> </label
        ><br />
        <label for="sms"
          >Не отправлять СМС.
          <input type="checkbox" v-model="sms" class="notreq"/></label
        ><br />
        <h1>Адрес</h1>
        <label for="index"
          >Индекс <input type="text" v-model="index" class="notreq"/></label
        ><br />
        <label for="country"
          >Страна <input type="text" v-model="country" class="notreq"/></label
        ><br />
        <label for="Region"
          >Облась <input type="text" v-model="Region" class="notreq"/></label
        ><br />
        <label for="City"
          >Город <input type="text" v-model="city" class="notreq"/></label
        ><br />
        <div class="error" v-if="!$v.city.required && !$v.city.$dirty">
          это поле обязательно
        </div>
        <label for="street"
          >Улица <input type="text" v-model="street" class="notreq"/></label
        ><br />
        <label for="House"
          >Дом <input type="text" v-model="House" class="notreq"/></label
        ><br />
        <h1>Паспорт</h1>
        <label for="document">
          Тип документа
          <select v-model="document">
            <option>Паспорт</option>
            <option>Свидетельство о рождении</option>
            <option>Водительские права</option>
          </select> </label
        ><br />
        <div class="error" v-if="!$v.document.required && !$v.document.$dirty">
          это поле обязательно
        </div>
        <label for="series">серия <input type="text" class="notreq"/></label
        ><br />
        <label for="number">номер <input type="text" class="notreq"/></label
        ><br />
        <label for="issuedBy"
          >кем выдан <input type="text" class="notreq"/></label
        ><br />
        <label for="dateOfIssue"
          >дата выдачи
          <input type="text" v-model="dateOfIssue" class="notreq"/></label
        ><br />
        <div
          class="error"
          v-if="!$v.dateOfIssue.required && !$v.dateOfIssue.$dirty"
        >
          это поле обязательно
        </div>
        <button type="submit" class="submit">
          отправить форму
        </button>
      </form>
    </div>
  </div>
</template>

<script>
import { required, minLength } from "vuelidate/lib/validators";
export default {
  name: "ValidationForm",
  data() {
    return {
      name: null,
      surname: null,
      patronymic: null,
      birthday: null,
      numberPhone: null,
      sex: null,
      groupClients: null,
      doctor: null,
      sms: false,
      city: null,
      index: null,
      country: null,
      Region: null,
      street: null,
      House: null,
      dateOfIssue: null,
      document: null
    };
  },
  validations: {
    surname: {
      required,
      minLength: minLength(2)
    },
    name: {
      required,
      minLength: minLength(2)
    },
    birthday: {
      required
    },
    numberPhone: {
      required,
      minLength: minLength(11)
    },
    groupClients: {
      required
    },
    city: {
      required
    },
    document: {
      required
    },
    dateOfIssue: {
      required
    }
  },
  methods: {
    submitForm() {
      if (!this.$v.$invalid) {
        alert("Вы успешно зарегистрировались");
        return {
          name: "",
          surname: "",
          patronymic: "",
          birthday: "",
          numberPhone: "",
          sex: "",
          groupClients: "",
          doctor: "",
          sms: "",
          city: "",
          index: "",
          country: "",
          Region: "",
          street: "",
          House: "",
          dateOfIssue: "",
          document: ""
        };
      } else {
        alert("пожалуйста заполните все поля");
      }
    }
  }
};
</script>

<style scoped lang="scss">
.SubmitForm {
  display: flex;
  justify-content: center;
  align-items: center;
  height: 900px;
}
.Form {
  background-color: #fff;
  border-radius: 15px;
  color: #000;
  overflow-y: scroll;
  height: 450px;
}
.formValidation {
  padding: 50px;
}
.error {
  color: red;
  font-size: 12px;
}
.notreq {
  margin-top: 15px;
}
.submit {
  margin-top: 20px;
}
</style>
