<template>
    <div>
      <phone-number-input
        v-model="phoneNumber"
        @country-changed="onCountryChanged"
        @input="validatePhoneNumber"
      ></phone-number-input>
      <span v-if="!validPhoneNumber" style="color: red;">Неверный номер телефона</span>
    </div>
  </template>
  
  <script>
  import PhoneNumberInput from 'vue-phone-number-input';
  import 'vue-phone-number-input/dist/vue-phone-number-input.css';
  
  
  export default {
    name: 'PhoneNumberInput',
    components: {
      PhoneNumberInput,
    },
    data() {
      return {
        phoneNumber: '',
        validPhoneNumber: true,
      };
    },
    methods: {
      onCountryChanged(countryCode) {
        // Действия при изменении страны
        console.log('Выбрана страна:', countryCode);
      },
      validatePhoneNumber() {
        // Валидация номера телефона
        this.validPhoneNumber = this.$refs.phoneNumberInput.phoneNumberValid();
      },
    },
  };
  </script>
  
  <style scoped>
  /*  добавить стилизацию компонента здесь */
  </style>
  