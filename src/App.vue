<template>
  <div id="app">
    <ValidationForm />
  </div>
</template>

<script>
import ValidationForm from "./components/ValidationForm";
export default {
  name: "App",
  components: { ValidationForm }
};
</script>

<style lang="scss">
#app {
  background-color: orange;
}
</style>
