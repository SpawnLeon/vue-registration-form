<template>
  <div id="app">
    <app-form></app-form>
  </div>

</template>

<script>

import AppForm from './components/AppForm.vue';

export default {
  name: 'App',
  components: {
    AppForm,

  },
  data() {
    return {};
  },
  methods: {},
};
</script>

<style lang="scss">

#app {
  font-family             : 'IBM Plex Sans', Helvetica, Arial, sans-serif;
  -webkit-font-smoothing  : antialiased;
  -moz-osx-font-smoothing : grayscale;
  display                 : flex;
  align-items             : center;
  justify-content         : center;
  height                  : 100vh;
  background-color        : #e5e5e5;
}

</style>
