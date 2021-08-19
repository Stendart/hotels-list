<template>
  <div id="app">
    <AppFilters :country="countryList"></AppFilters>
  </div>
</template>

<script>
  import hotels from "./assets/hotels.json";
  import country from "./assets/country.json";

  import AppFilters from './components/AppFilters';

export default {
  name: 'App',
  created() {
    console.log('test', hotels)
    console.log('country', country)
  },
  computed: {
    countryList() {
      return country;
    }
  },
  components: {
    AppFilters
  }
}
</script>

<style lang="scss">
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  /*text-align: center;*/
  color: #2c3e50;
  margin-top: 60px;
}
</style>
