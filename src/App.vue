<template>
  <the-header title="notebook"></the-header>
  <the-resource></the-resource>
</template>

<script>

import TheResource from "./components/learning-resources/TheResource";
import TheHeader from "./components/layouts/TheHeader";
export default {
  name: "App.vue",
  components: {
    TheHeader,
    TheResource
  },
}
</script>

<style>
* {
  box-sizing: border-box;
}

html {
  font-family: 'Roboto', sans-serif;
}

body {
  margin: 0;
}

</style>