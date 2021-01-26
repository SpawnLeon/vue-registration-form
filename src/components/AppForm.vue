<template>
  <form class="form"
        @submit.prevent="submitFormHandler">

    <header class="form__header">
      <div class="form__title">Регистрация</div>
      <div class="form__desc">
        Уже есть аккаунт? <a href="">Войти</a>
      </div>
    </header>
    <div class="form__inner">
      <app-input
        @input="$v.formData.name.$touch()"
        name="Имя"
        :error="$v.formData.name.$dirty && $v.formData.name.$invalid ? mes['invalid-value'] : ''"
        classes="form__item"
        placeholder="Введите Ваше имя"
        v-model.trim="formData.name"></app-input>

      <app-input
        @input="$v.formData.email.$touch()"
        name="Еmail"
        :error="$v.formData.email.$dirty && $v.formData.email.$invalid ? mes['invalid-value'] : ''"
        classes="form__item"
        placeholder="Введите ваш email"
        v-model.trim="formData.email"></app-input>

      <app-input
        @input="$v.formData.phone.$touch()"
        name="Номер телефона"
        :error="$v.formData.phone.$dirty && $v.formData.phone.$invalid ? mes['invalid-value'] : ''"
        classes="form__item"
        placeholder="Введите номер телефона"
        :mask="true"
        v-model.trim="formData.phone"></app-input>

      <app-select :languages="languages"
                  name="Язык"></app-select>

    </div>

    <footer class="form__footer">
      <app-checkbox classes="form__agree"></app-checkbox>
      <app-button classes="form__btn"
                  :disabled="!isValid">Зарегистрироваться
      </app-button>
    </footer>

  </form>
</template>

<script>

import {
  required,
  minLength,
  email,
  helpers,
} from 'vuelidate/lib/validators';

import AppButton from './AppButton.vue';
import AppCheckbox from './AppCheckbox.vue';
import AppInput from './AppInput.vue';
import AppSelect from './AppSelect.vue';

const fieldName = helpers.regex('alpha', /^[a-zA-Z- ]*$/);

export default {
  name: 'AppForm',
  components: {
    AppSelect,
    AppInput,
    AppCheckbox,
    AppButton,
  },
  data() {
    return {
      formData: {
        name: '',
        email: '',
        phone: '',
        language: '',
      },

      languages: [
        'Русский',
        'Английский',
        'Китайский',
        'Испанский',

      ],
      mes: {
        'invalid-value': 'Введено не корректное значение',
      },
    };
  },
  computed: {
    isValid() {
      return !this.$v.$invalid;
    },
  },
  methods: {
    submitFormHandler() {
      alert('The form has been submitted');
    },
  },
  validations: {
    formData: {
      name: {
        required,
        minLength: minLength(1),
        fieldName,
      },
      email: {
        required,
        email,
      },
      phone: {
        required,
        minLength: minLength(18),
      },
    },

  },

};
</script>

<style scoped
       lang="scss">
.form {
  min-width        : 360px;
  max-width        : 460px;
  width            : 100%;
  background-color : #fff;
  box-shadow       : 0px 12px 24px rgba(44, 39, 56, 0.02), 0px 32px 64px rgba(44, 39, 56, 0.04);
  border-radius    : 24px;
  padding          : 40px 30px;

  // .form__header
  &__header {
    margin-bottom : 52px;

  }

  // .form__title
  &__title {
    font-weight : bold;
    font-size   : 34px;
    line-height : 1.2941;
    color       : #2c2738;
  }

  // .form__desc
  &__desc {
    font-size   : 16px;
    line-height : 1.37;
    color       : #2c2738;
    margin-top  : 8px;

    > a {
      text-decoration : none;
      color           : #0880ae;
    }
  }

  // .form__item
  &__item {
    margin-top : 8px;

    &:first-child {
      margin-top : 0;
    }
  }

  // .form__agree
  &__agree {
    margin-top : 31px;
  }

  // .form__btn
  &__btn {
    margin-top : 38px;
  }

}
</style>
