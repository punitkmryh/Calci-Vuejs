<template>
  <div id="app">
    <img src="./assets/logo.png" class="logo" />
    <h2 class="header">Vue.js Calculator</h2>
    <vue-typer
      text="Hi There 👨🏻‍💻! This is Demo of a simple VueJS Calcualtor 🀫"
      :repeat="Infinity"
      :shuffle="false"
      initial-action="typing"
      :pre-type-delay="70"
      :type-delay="70"
      :pre-erase-delay="2000"
      :erase-delay="250"
      erase-style="backspace"
      :erase-on-complete="false"
      caret-animation="expand"
    ></vue-typer>
    <calculator />
  </div>
</template>

<script>
import calculator from "./components/calculator";
import { VueTyper } from "vue-typer";

export default {
  name: "App",
  components: {
    calculator,
    VueTyper,
  },
};
</script>

<style>
#app {
  font-family: Karla, sans-serif;
  /* -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale; */
  text-align: center;
  color: #2c3e50;
  margin-top: 30px;
}
.logo {
  display: block;
  margin: 20px auto;
  height: 75px;
}
.vue-typer {
  font-size: 16px;
  font-weight: bold;
}

.header {
  color: rgb(59, 55, 52);
  font-weight: 800;
}
</style>
