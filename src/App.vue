<template>
  <div id="app">
    <AppHeader/>
    <Slider/>
    <div class="logo">
      <a href="#"></a>
    </div>
  </div>
</template>

<script>
import Slider from "./components/Slider";
import AppHeader from "./components/AppHeader";

export default {
  name: 'app',
  components: {
    Slider,
    AppHeader
  }
}
</script>

<style>
* {
  margin: 0;
  padding: 0;
  box-sizing: border-box;
}
a {
  text-decoration: none;
  color: inherit;
}
ul {
  list-style: none;
}
li {
  display: inline-block;
}
#app {
  font-family: monospace;
  text-align: center;
  color: #2c3e50;
  position: relative;
}
</style>
