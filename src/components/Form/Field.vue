<!-- create a field component for formik which is a slot and need to be dynamic -->
<!--this component need to be dynamic-->
<!--this component need to be able to render different types of inputs-->

<template>
  <div>
    <label :for="name">{{ label }}</label>
    <input v-model:name :id="name" :name="name" :value="value" @input="handleChange" :type="formtype" />
  </div>
</template>

<script>
const Field = {
  name: "",
  label: "",
  formtype: "",
  value: "",
  handleChange: "",
};

</script>