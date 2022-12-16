<template>
  <slot
      :values="values"
      :submit="handleSubmit"
      :isSubmitting="isSubmitting"
      :errors="errors"
      :set="set"
  ></slot>
</template>

<script setup>
import {defineProps, ref} from "vue";
import {provide} from "vue";

const props = defineProps({
  initialValues: {
    type: Object,
  },
  validate: {
    type: Function,
  },
  onSubmit: {
    type: Function,
  }
});

const values = ref(props.initialValues);
//create a ref for errors
const errors = ref([]);
const isSubmitting = ref(false);

const handleSubmit = () => {
  try {
    props.validate(values.value);
  } catch (e) {
    errors.value = e.errors;
    // errors.push(e.error);
  }finally {
    if (errors.value.length === 0) {
      props.onSubmit(values.value);
    }
  }
}

function set(name, value) {
  console.log('formik',name, value)
  values.value[name] = value;
  errors.value = [];
}

provide("formikProvider", {
  set,
  values,
});

</script>