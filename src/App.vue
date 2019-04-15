<template>
  <div id="app">
    <Nav/>
    <Header/>
    <Press/>
    <Web/>
    <Tv/>
    <Radio/>
    <Footer/>
  </div>
</template>

<script>
import Header from "./components/Header.vue";
import Test from "./components/Test.vue";
import Nav from "./components/Nav.vue";
import Card from "./components/Card.vue";
import Press from "./components/Press.vue";
import Web from "./components/Web.vue";
import Radio from "./components/Radio.vue";
import Tv from "./components/Tv.vue";
import Footer from "./components/Footer";

export default {
  name: "app",

  components: {
    Header,
    Card,
    Nav,
    Press,
    Web,
    Radio,
    Tv,
    Footer
  }
};
</script>

<style>
body {
  margin: 0px;
}
#app {
  font-family: "Avenir", Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
}

section {
  padding-top: 30px;
}
h2 {
  font-family: "Bubblegum Sans", cursive;
}
</style>
