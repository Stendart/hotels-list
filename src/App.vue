<template>
  <div id="app">
    <main class="main">
      <AppFilters :country="countryList" class="filter-wrapper"
                  @changeCountryList="setCountryList"
                  @changeType="setTypes"
                  @changeStars="setStars"
                  @changeReviewsCount="setReviewsCount"
                  @changePriceRange="setPriceRange"

                  @applyFilters="applyFilters"></AppFilters>
      <HotelsList v-if="hotelsList.length" :hotels="hotelsList" class="data-wrapper"></HotelsList>
      <h3 v-else class="data-wrapper data-text">Записей не найдено</h3>
    </main>
  </div>
</template>

<script>
import hotels from "./assets/hotels.json";
import country from "./assets/country.json";

import AppFilters from './components/AppFilters';
import HotelsList from './components/HotelsList';

export default {
  name: 'App',
  data() {
    return {
      hotels: hotels.hotels,
      filtersParams: null,

      selectCountryList: [],
      selectTypeList: [],
      selectStars: [],
      reviewsCount: 0,
      priceRange: {},
    }
  },
  methods: {
    setCountryList(list) {
      this.selectCountryList = list;
    },
    setTypes(list) {
      this.selectTypeList = list;
    },
    setStars(list) {
      this.selectStars = list;
    },
    setReviewsCount(count) {
      this.reviewsCount = count;
    },
    setPriceRange(range) {
      this.priceRange = range;
    },

    applyFilters(filtersParams) {
      this.filtersParams = filtersParams;
    },

    filteredByParam(arr, fieldName, param) {
      return arr.filter(el => {
        return param.includes(el[fieldName]);
      })
    },
    filteredByCompaire(arr, fieldName, param1, param2) {
      if(!param2) {
        return arr.filter(el => {
          return el[fieldName] > param1;
        })
      } else {
        return arr.filter(el => {
          return el[fieldName] > param1 && el[fieldName] < param2;
        })
      }
    }
  },
  computed: {
    countryList() {
      return country;
    },
    hotelsList() {
      if(!this.filtersParams) {
        return this.hotels;
      }

      const filteredByCountry = this.filteredByParam(this.hotels, 'country', this.filtersParams.selectCountryList);
      const filteredByType = this.filteredByParam(filteredByCountry, 'type', this.filtersParams.selectTypeList);
      const filteredByStars = this.filteredByParam(filteredByType, 'stars', this.filtersParams.selectStars);

      const filteredByReviews = this.filteredByCompaire(filteredByStars, 'reviews_amount', this.filtersParams.reviewsCount);
      const filteredByPrice = this.filteredByCompaire(filteredByReviews, 'min_price', this.filtersParams.priceRange[0], this.filtersParams.priceRange[1])
      return filteredByPrice;
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
  .data-wrapper {
    width: 65%;
  }
  .data-text {
    text-align: center;
  }
</style>
