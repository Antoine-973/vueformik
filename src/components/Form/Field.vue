<script>

export default {
  name: "Field",
  inject: ["formikProvider"],
  props: {
    name: {
      type: String,
      required: true,
    },
    as: {
      type: String || Object,
      default: "input",
    },
  },
  methods: {
    handleInput(e) {
      this.formikProvider.set(this.name, e.target.value);
    },
  },
};

</script>

<template>
  <component :is="as" :name="name" :value="formikProvider.values.value[name]" @input="handleInput" />
</template>