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

const handleSubmit = () => {
  console.log(values.value);
  if (props.validate(values.value)) {
    props.onSubmit(values.value);
    isSubmitting.value = true;
  } else {
    errors.value = props.validate(values.value);
  }
}

const values = ref(props.initialValues);
const errors = ref([]);
const isSubmitting = ref(false);

function set(name, value) {
  values.value.name = value;
}

provide("formikProvider", {
  set,
  values,
});

</script>