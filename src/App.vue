<template>
  <div id="app" style="display: flex; justify-content: center; align-items: center; height: 100vh;">
    <div>
      <select v-model="selectedCountry" @change="onCountryChanged">
        <!-- Добавляем v-bind:key к каждой опции -->
        <option v-for="country in countries" :key="country.code" :value="country.code">{{ country.name }}</option>
      </select>
      <phone-number-input
        v-model="phoneNumber"
        :country="selectedCountry"
        @input="validatePhoneNumber"
      ></phone-number-input>
      <span v-if="!validPhoneNumber" style="color: red;">Неверный номер телефона</span>
    </div>
  </div>
</template>

<script>
import PhoneNumberInput from 'vue-phone-number-input';
import 'vue-phone-number-input/dist/vue-phone-number-input.css';

export default {
  name: 'App',
  components: {
    PhoneNumberInput,
  },
  data() {
    return {
      phoneNumber: '',
      validPhoneNumber: true,
      selectedCountry: 'US', // Задайте страну по умолчанию
      countries: [ // Список стран
        { code: 'US', name: 'United States' },
        { code: 'GB', name: 'United Kingdom' },
        // Другие страны...
      ]
    };
  },
  methods: {
    onCountryChanged() {
      // Действия при изменении страны
    },
    validatePhoneNumber() {
      // Валидация номера телефона
      this.validPhoneNumber = this.$refs.phoneNumberInput.phoneNumberValid();
    },
  },
};
</script>

<style>
/*  стили */
</style>
