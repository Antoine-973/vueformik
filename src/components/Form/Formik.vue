<template>
  <div>
    <h1>Formik</h1>
    <form @submit.prevent="onSubmit">
      <slot :values="values" :handleChange="handleChange" :handleSubmit="handleSubmit" />
      <Field name="" label="" formtype="" />
    </form>
  </div>
</template>

<script>
import Field from "./Field.vue";
import yup from "yup";

const initialValues = {
  name: "",
  email: "",
  password: "",
};

const validationSchema = yup.object({
  name: yup.string().required(),
  email: yup.string().email().required(),
  password: yup.string().min(8).required(),
});

export default {
  name: "Formik",
  components: {
    Field,
  },
  props: {
    initialValues: {
      type: Object,
      default: () => initialValues,
    },
    validationSchema: {
      type: Object,
      default: () => validationSchema,
    },
    onSubmit: {
      type: Function,
      default: () => {},
    },
  },
  setup(props) {
    const values = ref(props.initialValues);
    const errors = ref({});
    const touched = ref({});
    const handleChange = (e) => {
      values.value[e.target.name] = e.target.value;
    };
    const handleSubmit = (e) => {
      e.preventDefault();
      props.onSubmit(values.value);
    };
    return {
      values,
      errors,
      touched,
      handleChange,
      handleSubmit,
    };
  },
};

</script>