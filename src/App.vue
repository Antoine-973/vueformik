<!--
  Vue 3 Composition API
  <script>
  import HelloWorld from "./components/HelloWorld.vue";
  import TheWelcome from "./components/TheWelcome.vue";
  import MyButton from "./components/MyButton.vue";


  export default {
    name: "App",
    components: {
      HelloWorld,
      TheWelcome,
      MyButton
    },
    setup() {
      const content = "<h1>Content</h1>";
      return {
        content
      };
    }
  }
  </script>
-->

<!--
  Vue 2 ou Vue 3 Options API
  <script>
  import HelloWorld from "./components/HelloWorld.vue";
  import TheWelcome from "./components/TheWelcome.vue";
  import MyButton from "./components/MyButton.vue";

  export default {
    name: "App",
    components: {
      HelloWorld,
      TheWelcome,
      MyButton
    }
  }
  </script>
-->
<script setup>

const initialValues = {
  lastname: "",
  firstname: "",
  email: "",
};

</script>

<template>
  <!--
    <Formik
        initialValues={{
        firstName: '',
    lastName: '',
    email: '',
    }}
    onSubmit={async (values) => {
    await new Promise((r) => setTimeout(r, 500));
    alert(JSON.stringify(values, null, 2));
    }}
    >
    <Form>
      <label htmlFor="firstName">First Name</label>
      <Field id="firstName" name="firstName" placeholder="Jane" />

      <label htmlFor="lastName">Last Name</label>
      <Field id="lastName" name="lastName" placeholder="Doe" />

      <label htmlFor="email">Email</label>
      <Field
          id="email"
          name="email"
          placeholder="jane@acme.com"
          type="email"
      />
      <button type="submit">Submit</button>
    </Form>
    </Formik>
  -->


  <Formik :initial-values="initialValues" :validation-schema :onSubmit>
    <Field></Field>
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
