<template>
  <h1 class="heading-1">Inputs</h1>
  <form @submit.prevent="submitForm">
    <Input
      label="Your name"
      name="name"
      placeholder="Input your name"
      v-model:value="v.nameField.$model"
      :error="v.nameField.$errors"
    />
    <Input
      label="Your email"
      name="email"
      placeholder="Input your email"
      v-model:value="v.emailField.$model"
      :error="v.emailField.$errors"
    />
    <Input
      label="Your lucky number"
      name="luckynumber"
      placeholder="Input your lucky number"
      v-model:value="v.luckyField.$model"
      :error="v.luckyField.$errors"
    />
    <Input
      label="Your password"
      name="password"
      type="password"
      placeholder="Input your password"
      v-model:value="passwordField"
    />
    <Input
      label="Confirm password"
      name="confirmpassword"
      type="confirmpassword"
      placeholder="Input your password again"
      v-model:value="v.confirmPasswordField.$model"
      :error="v.confirmPasswordField.$errors"
    />
    <Input
      label="Enter string with 'frontend'"
      name="frontend"
      type="frontend"
      placeholder="Enter string with 'frontend'"
      v-model:value="v.frontendField.$model"
      :error="v.frontendField.$errors"
    />
    <Button label="Submit" color="primary" />
  </form>
</template>
<script setup>
import { ref, computed } from "vue";
import Input from "@/components/Input.vue";
import useVuelidate from "@vuelidate/core";
import Button from "@/components/Button.vue";
import {
  minLength,
  helpers,
  email,
  numeric,
  maxLength,
  sameAs,
  required
} from "@vuelidate/validators";
const nameField = ref("");
const emailField = ref("");
const luckyField = ref("");
const passwordField = ref("");
const confirmPasswordField = ref("");
const frontendField = ref("");

const mustBeFrontend = (val) => {
  return val.includes("frontend");
};

const rules = computed(() => {
  return {
    nameField: {
      minLength: helpers.withMessage(
        "Минимальная длина 3 символа",
        minLength(3)
      ),
      required: helpers.withMessage(
        "Это обязательное поле",
       required
      ),
    },
    emailField: {
      email: helpers.withMessage("Введите корректный email", email),
    },
    luckyField: {
      numeric: helpers.withMessage("Введите число!", numeric),
      maxLength: helpers.withMessage(
        "Максимальная длина 3 символа",
        maxLength(3)
      ),
    },
    confirmPasswordField: {
      sameAsPassword: helpers.withMessage(
        "Пароли не совпадают",
        sameAs(passwordField.value)
      ),
    },
    frontendField: {
      frontendField: helpers.withMessage(
        'Поле должно содержать слово "frontend"',
        mustBeFrontend
      ),
    },
  };
});

const v = useVuelidate(rules, {
  nameField,
  emailField,
  luckyField,
  confirmPasswordField,
  frontendField,
});

function submitForm() {
  v.value.$touch();
  if (v.value.$error) {
    return;
  } else {
    alert("Form submited!");
  }
}
</script>
<style lang="scss" scoped></style>
