<script setup>

import * as yup from "yup";
import Formik from "./components/Form/Formik.vue";
import Field from "./components/Form/Field.vue";
import Captcha from "./components/Captcha.vue"

const initialValues = {
  name: "fiuezhuifzh",
};

const validationSchema = yup.object({
  name: yup.string(),
});

const onSubmit = (values) => {
  console.log("YAAAAAAAAAAAAA", values);
}

const options = Array.from({ length: 9 }, (_, i) => ({
  id: i,
  href: `https://picsum.photos/200?random=${i}`,
}));

</script>
<template >
  <Formik v-slot="{formik,submit}" :initialValues="initialValues" :validate="(values) => validationSchema.validateSync(values)" @submit="onSubmit">
    <form @submit.prevent="submit">
      <Field name="name" as="input" />
      <Field name="captcha" :as="Captcha" v-model="captcha" :options="options"/>
      <button type="submit">Submit</button>
    </form>
  </Formik>
</template>