<script setup>
import {defineProps} from "vue";

defineProps({
  name: {
    type: String,
    required: true,
  },
  label: {
    type: String,
    required: true,
  },
  placeholder: {
    type: String,
    required: true,
  },
  value: {
    type: Object,
    required: true,
  },
  type: {
    type: String,
    required: true,
  },
});
</script>
<script>
  export default {
    name: "Field",
    setup(props) {
      const handleChange = (e) => {
        console.log(e.target.value);
        props.value[e.target.name] = e.target.value;
      };
      return {
        props,
        handleChange,
      };
    },
  };
</script>
<template>
  <div>
    <label :for="name">{{ label }}</label>
    <input v-model="name" :id="name" :name="name" :value="value" @input="handleChange" :type="type" :placeholder="placeholder"/>
  </div>
</template>

