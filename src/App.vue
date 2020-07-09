<template>
  <div id="app">
    <app-header></app-header>
    <app-nav></app-nav>
    <app-main></app-main>
  </div>
</template>

<script>
import Header from './components/header/Header';
import Nav from './components/nav/Nav';
import Main from './components/main/Main';

export default {
  components: {
    appHeader: Header,
    appMain: Main,
    appNav: Nav
  }
}
</script>

<style lang="scss">
html, body {
  margin: 0;
  padding: 0;
  scroll-snap-type: mandatory;
  scroll-snap-points-y: repeat(100vh);
  scroll-snap-type: y mandatory;

  ::-webkit-scrollbar {
    display: none;
  }
}

#app {
  font-family: 'Avenir', Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
}
</style>
