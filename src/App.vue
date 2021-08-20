<template>
  <div id="app">
    <main class="main">
      <AppFilters :country="countryList" class="filter-wrapper"></AppFilters>
      <HotelsList :hotels="hotelsList" class="hotel-wrapper"></HotelsList>
    </main>
  </div>
</template>

<script>
  import hotels from "./assets/hotels.json";
  import country from "./assets/country.json";

  import AppFilters from './components/filters/AppFilters';
  import HotelsList from './components/HotelsList';

export default {
  name: 'App',
  created() {
    console.log('test', hotels)
    console.log('country', country)
  },
  computed: {
    countryList() {
      return country;
    },
    hotelsList() {
      return hotels.hotels;
    }
  },
  components: {
    AppFilters,
    HotelsList
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

  .main {
    display: flex;
    justify-content: space-between;

    width: 90%;
    margin: 0 auto;
  }

  .filter-wrapper {
    width: 30%;
  }
  .hotel-wrapper {
    width: 65%;
  }
</style>
