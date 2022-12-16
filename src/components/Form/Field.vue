<script setup>
import {defineProps, inject} from "vue";

const props = defineProps({
  name: {
    type: String,
    required: true,
  },
  as: {
    type: String || Object,
    default: "input",
  },
});

const formikData = inject("formikProvider");

const handleInput = (e) => {
  formikData.set(props.name, e.target.value);
}

const handleComponent = (e) => {
  formikData.set(props.name, e)
}

</script>

<template>
  <component v-if="typeof as === 'string'"
             :is="as" :name="name"
             :value="formikData.values.value[name]" @input="handleInput"/>

  <component v-else :is="as" :name="name"
             :modelValue="formikData.values.value[name]" v-on:update:modelValue="handleComponent"/>
</template>