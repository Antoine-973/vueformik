<script setup>

import * as yup from "yup";
import Formik from "./components/Form/Formik.vue";
import Field from "./components/Form/Field.vue";
import Captcha from "./components/Captcha.vue"

const initialValues = {
  name: "",
};

const validationSchema = yup.object({
  name: yup.string().min(3).max(15).required(),
});

const onSubmit = (values) => {
  alert("Votre formulaire s'est bien envoyé \n" + JSON.stringify(values));
}

const options = Array.from({length: 9}, (_, i) => ({
  id: i,
  href: `https://picsum.photos/200?random=${i}`,
}));

</script>

<template>
  <h1>Projet tp formik</h1>
  <Formik v-slot="{formik,submit,errors, isSubmitting}" :initialValues="initialValues"
          :validate="(values) => validationSchema.validateSync(values)" @submit="onSubmit">
    <form @submit.prevent="submit">
      <div>
        <Field name="name" as="input"/>
        <Field name="captcha" :as="Captcha" v-model="captcha" :options="options"/>
        <button :disabled="isSubmitting" type="submit">Submit</button>
      </div>
      <div>
        <template v-for="error in errors">
          <p style="color: #d95a5a">{{ error }}</p>
        </template>
      </div>
    </form>
  </Formik>
</template>