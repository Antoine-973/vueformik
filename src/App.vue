<script setup>

import * as yup from "yup";
import Formik from "./components/Form/Formik.vue";
import Field from "./components/Form/Field.vue";
import {ref} from "vue";

const initialValues = ref({
  name: "",
  email: "",
  password: "",
});

const validationSchema = yup.object({
  name: yup.string().required(),
  email: yup.string().email().required(),
  password: yup.string().min(8).required(),
});

</script>
<template v-slot="defaut">

  <Formik :initial-values="initialValues" :validation-schema="validationSchema" :onSubmit="()=>{}">
    <form>
      <Field name="name" label="Name" formtype="date" placeholder="antoine la merde"/>
      <button type="submit">Submit</button>
    </form>
  </Formik>
</template>

<style scoped>
header {
  line-height: 1.5;
}

.logo {
  display: block;
  margin: 0 auto 2rem;
}

@media (min-width: 1024px) {
  header {
    display: flex;
    place-items: center;
    padding-right: calc(var(--section-gap) / 2);
  }

  .logo {
    margin: 0 2rem 0 0;
  }

  header .wrapper {
    display: flex;
    place-items: flex-start;
    flex-wrap: wrap;
  }
}
</style>
