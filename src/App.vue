<template>
  <div id="app">
    <Accordion />
  </div>
</template>

<script>
import Accordion from "./components/Accordion";

export default {
  name: "App",
  components: {
    Accordion
  }
};
</script>

<style>
@import url("https://fonts.googleapis.com/css?family=Montserrat:400,400i,700");
html, body, #app {
  color: #727272;
  font-family: Montserrat, sans-serif;
  font-size: 14px;
  width: 100%;
  height: 100%;
  padding: 0;
  margin: 0;
}

#app,
.accordion,
.accordion-item,
.accordion-header,
.accordion-body {
  font-family: inherit;
}

#app {
  background-color: #82dfff;
  display: flex;
  box-sizing: border-box;
}

</style>
