<template>
  <div>
    <!-- form with all Fields pass to the Formik component -->
    <slot></slot>
  </div>
</template>

<script>
import Field from "./Field.vue";
import {ref} from "vue";

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
    const handleChange = (e) => {
      values.value[e.target.name] = e.target.value;
    };
    const handleSubmit = (e) => {
      e.preventDefault();
      props.onSubmit(values.value);
    };
    return {
      values,
      props,
      handleChange,
      handleSubmit,
    };
  },
};

</script>