<template>
  <div id="app">
    <agenda/>
  </div>
</template>

<script>
import './index.scss';
import Agenda from './components/Agenda';

export default {
  name: 'App',
  components: {
    Agenda,
  },
};
</script>

<style>
#app {
  font-family: "Avenir", Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
